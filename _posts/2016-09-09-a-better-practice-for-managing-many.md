---
title: 'A Better Practice for Managing Many Extras_require Dependencies in Python'
date: 2019-11-10T08:31:00+01:00
draft: false
---

Background
----------

One problem I was facing when building [GNES: Generic Neural Elastic Search](https://github.com/gnes-ai/gnes/) is how to effectively control the dependencies in Python. The main dependencies of GNES is very simple: `numpy`, `grpcio`, `pyzmq` and a YAML parser. But this only runs a vanilla GNES with no fancy deep learning models nor preprocessors. As GNES aims to provide a generic solution for multi-modality semantic search, it often requires extra packages from different domains, such as NLP and CV. Apparently, these optional dependencies are not required for all uses of GNES: people who use GPT2 as text encoder may require `pytorch-transformer` but not `opencv` and Tensorflow. We already know that `setuptools` provides a `extras_require` field that allows you to [define those plugin-like dependencies](https://setuptools.readthedocs.io/en/latest/setuptools.html#declaring-extras-optional-features-with-their-own-dependencies) as following:  

```
1  
2  
3  
4  
5  
6  
7  
8  
9  

```

```
setup(  
 name='GNES',  
 ...  
 extras\_require={  
 'bert': \['bert-serving-server>=1.8.6', 'bert-serving-client>=1.8.6', 'pytorch-transformer', 'flair'\],  
 'vision': \['opencv-python>=4.0.0', 'imagehash>=4.0', 'image', 'peakutils'\],  
 ...  
 }  
)  

```

This allows one to later cherry-pick the feature via `pip install gnes[bert]`. However, in practice I found difficult to maintain this feature map as it grows due to the following problems:

*   a package can enable multiple features, but I don’t want to copy-paste the same string `opencv-python>=4.0.0` to everywhere;
*   the same feature can be enabled by different packages, but often users only install the one _they_ preferred. See `bert` in the last example;
*   it is not straightforward to see which features a package enabled and what consequences if this package is broken/removed/badly-licensed;
*   unable to install all dependencies via `pip install gnes[all]`;
*   hardcoding this big map in `setup.py` is cumbersome. By decoupling them I can version-control each one better.

Anyhow, if you dislike something, you always find thousands of reasons to dislike it.

Solution: Build an “Inverted Index”
-----------------------------------

The solution that I figured out is simple but effective: maintain a _package-to-feature_ map in a separate plain text file, then parse it to an _inverted_ map in `setup.py`. So inverted index, kind of. For example, my [`extra-requirements.txt` looks like the following](https://github.com/hanxiao/gnes/blob/master/extra-requirements.txt):  

```
1  
2  
3  
4  
5  
6  
7  
8  
9  
10  
11  
12  
13  
14  
15  
16  
17  
18  
19  
20  
21  
22  
23  
24  
25  
26  

```

```
\# FORMAT  
\# Put your extra requirements here in the following format  
#  
\# package\[version\_required\]: tag1, tag2, ...  
  
bert-serving-server>=1.8.6: bert, nlp, encode  
bert-serving-client>=1.8.6: bert, nlp, encode  
flair>=0.4.1: nlp, bert, encode  
annoy==1.15.2: index  
jieba: chinese, nlp  
opencv-python>=4.0.0: cv, prep  
imagehash>=4.0: cv  
image: cv  
peakutils: cv  
plyvel>=1.0.5: index  
pylint: test  
memory\_profiler>=0.55.0: test  
psutil>=5.6.1: test  
gputil>=1.4.0: gpu  
pytorch-transformers: nlp, bert, encode  
onnxruntime: encode, ml  
librosa>=0.7.0: audio  
scipy: numeric  
sklearn: ml  
flask: http  
aiohttp: http  

```

If you work with an open governance model, you may want to set up some guidelines in

`CONTRIBUTING`

about the feature tags, so that other contributors can follow, e.g.:

  
*   always reuse the existing feature tags if possible;
  
*   when create a new tag, keep it alphabetical, short and general;
  
*   tag order does not matter, and duplicated tag will be ignored.
  

Now here is my parser to “invert” this map into the format that `extras_require` needs:

```
1  
2  
3  
4  
5  
6  
7  
8  
9  
10  
11  
12  
13  
14  
15  
16  
17  
18  
19  
20  
21  
22  
23  

```

```
  
  
def get\_extra\_requires(path, add\_all=True):  
 import re  
 from collections import defaultdict  
  
 with open(path) as fp:  
 extra\_deps = defaultdict(set)  
 for k in fp:  
 if k.strip() and not k.startswith('#'):  
 tags = set()  
 if ':' in k:  
 k, v = k.split(':')  
 tags.update(vv.strip() for vv in v.split(','))  
 tags.add(re.split('\[<=>\]', k)\[0\])  
 for t in tags:  
 extra\_deps\[t\].add(k)  
  
    
 if add\_all:  
 extra\_deps\['all'\] = set(vv for v in extra\_deps.values() for vv in v)  
  
 return extra\_deps  

```

, which returns a map as follows:

```
1  
2  
3  
4  
5  
6  

```

```
bert: {'pytorch-transformers', 'flair>=0.4.1', 'bert-serving-server>=1.8.6', 'bert-serving-client>=1.8.6'}  
nlp: {'flair>=0.4.1', 'bert-serving-server>=1.8.6', 'jieba', 'pytorch-transformers', 'bert-serving-client>=1.8.6'}  
bert-serving-server: {'bert-serving-server>=1.8.6'}  
encode: {'onnxruntime', 'flair>=0.4.1', 'bert-serving-server>=1.8.6', 'pytorch-transformers', 'bert-serving-client>=1.8.6'}  
...  
all: {'onnxruntime', 'annoy==1.15.2', 'imagehash>=4.0', 'psutil>=5.6.1', 'librosa>=0.7.0', 'sklearn', 'aiohttp', 'pytorch-transformers', 'peakutils', 'image', 'pylint', 'bert-serving-server>=1.8.6', 'gputil>=1.4.0', 'bert-serving-client>=1.8.6', 'scipy', 'flair>=0.4.1', 'flask', 'memory\_profiler>=0.55.0', 'opencv-python>=4.0.0', 'jieba', 'plyvel>=1.0.5'}  

```

A nice thing about this solution is that you can add sophisticated logic in the parse function to enable fancy features. In this example, I use the canonical package name as the feature tag (e.g. `annoy: [annoy==1.15.2]`), and add tag `all` to allow a full installation via `pip install .[all]`. You can also add logic to improve granularity of the tags, or introduce hierarchies to them. Just remember to assign it to `extras_require` in your `setup` construct:  

```
1  
2  
3  
4  
5  

```

```
setup(  
 name='GNES',  
 ...  
 extras\_require=get\_extra\_requires('extra-requirements.txt'),  
)  

```

The complete example [can be found here](https://github.com/hanxiao/gnes).

Conclusion
----------

In this article, I introduce a simple yet effective solution to manage optional dependencies via `extras_require` in Python. This method is particularly useful when you have too many optional dependencies and you want users to install them as plugins or on-demand features. Comparing to the traditional method where we hardcode a big feature map in `setup.py`, this method is more readable and easier to maintain.

Managing a readable `setuptools` script is probably not on the priority list of every (or _any_?) AI engineer, still I think it is a nice little trick to keep in mind and make life a bit easier. I’m not going to call it _the best practice_ because that would be way ambitious. So a better practice it is (than [what described in the documentation](https://setuptools.readthedocs.io/en/latest/setuptools.html#declaring-extras-optional-features-with-their-own-dependencies)).

That said, in GNES we actually have a more sustainable way to manage AI model dependencies via Docker containers, including required Python packages, deep learning framework, pretrained models, hyperparameters and GPU drivers. Everything is wrapped in one container, and the model developers enjoys the full autonomy. This concept is what I called [_Model as Docker, and Docker as a Plugin_](https://hanxiao.io/2019/07/29/Generic-Neural-Elastic-Search-From-bert-as-service-and-Go-Way-Beyond/#model-as-docker-and-docker-as-a-plugin). Interested readers are recommended to checkout [GNES Hub](https://github.com/gnes-ai/hub) and find out how to use it in GNES.

![](https://hanxiao.io/2019/11/07/A-Better-Practice-for-Managing-extras-require-Dependencies-in-Python/4fae4a63.png "Model as Docker, and Docker as a Plugin")

  
  
from Hacker News https://ift.tt/2WTdUqK