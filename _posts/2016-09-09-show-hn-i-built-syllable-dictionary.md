---
title: 'Show HN: I built a syllable dictionary using Python and web scraping'
date: 2019-10-06T02:46:00+01:00
draft: false
---

![](https://zacs.site/blog/favicon.ico "  Building a Syllable Dictionary with Python - Zac J. Szewczyk  ")  

By Zac J. Szewczyk on [2019](https://zacs.site/blog/2019.html)/[10](https://zacs.site/blog/2019-10.html)/04 19:19:07 EST

As most projects do, this one started small. I already had a way to preview Markdown files. [Proofer](https://zacs.site/projects.html#proofer) also counts words, sentences, and paragraphs, then averages those values and estimates reading time. The script finds [complex or overused phrases](http://www.plainenglish.co.uk/the-a-z-of-alternative-words.html), and highlights repeated words, be verbs, and adverbs that make for weak writing, too. It also calculates the Gunning Fog Index, and scores for the Flesch-Kincaid reading ease and grade level tests. I built this script to give me a few more features than [Marked](https://marked2app.com/), which I had used to proof my writing for years. It worked well, but runtime shot up if it had to process posts with more than a few hundred words. I set out to fix this, and ended up building an entire syllable dictionary in Python. Proofer has still not gotten any faster.

Proofer had no trouble with small files, but runtime shot up if it had to process posts with more than a few hundred words. Runtime went up as word count did, and so I started hunting for performance wins in [the 129-line method that counted syllables](https://github.com/eaydin/sylco/blob/master/sylco.py). Called for every word in the source file but not optimized for speed or memory use, this seemed like a good place to start.

### The Original Syllable Counter

Counting syllables seems easy. Spend some time looking for [examples](https://stackoverflow.com/questions/9096228/counting-syllables-in-a-word) of [others](https://stackoverflow.com/questions/46759492/syllable-count-in-python) doing [this](http://shallowsky.com/blog/programming/count-syllables-in-python.html), though, and you will soon realize that the English language makes this quite hard. I did not want to sink a ton of time into this, so I used this script from Emre Aydin.

```
 1 2 3 4 5 6 7 8 9 10 11 12 13 14 15 16 17 18 19 20 21 22 23 24 25 26 27 28 29 30 31 32 33 34 35 36 37 38 39 40 41 42 43 44 45 46 47 48 49 50 51 52 53 54 55 56 57 58 59 60 61 62 63 64 65 66 67 68 69 70 71 72 73 74 75 76 77 78 79 80 81 82 83 84 85 86 87 88 89 90 91 92 93 94 95 96 97 98 99 100 101 102 103 104 105 106 107 108 109 110 111 112 113 114 115 116 117 118 119 120 121 122 123 124 125 126 127 128 129
```

```
def sylco(word) : word \= word.lower() exception\_add \= \['serious','crucial'\] exception\_del \= \['fortunately','unfortunately'\] co\_one \= \['cool','coach','coat','coal','count','coin','coarse','coup','coif','cook','coign','coiffe','coof','court'\] co\_two \= \['coapt','coed','coinci'\] pre\_one \= \['preach'\] syls \= 0 disc \= 0 if len(word) <= 3 : syls \= 1 return syls if word\[\-2:\] \== "es" or word\[\-2:\] \== "ed" : doubleAndtripple\_1 \= len(re.findall(r'\[eaoui\]\[eaoui\]',word)) if doubleAndtripple\_1 \> 1 or len(re.findall(r'\[eaoui\]\[^eaoui\]',word)) \> 1 : if word\[\-3:\] \== "ted" or word\[\-3:\] \== "tes" or word\[\-3:\] \== "ses" or word\[\-3:\] \== "ied" or word\[\-3:\] \== "ies" : pass else : disc+=1 le\_except \= \['whole','mobile','pole','male','female','hale','pale','tale','sale','aisle','whale','while'\] if word\[\-1:\] \== "e" : if word\[\-2:\] \== "le" and word not in le\_except : pass else : disc+=1 doubleAndtripple \= len(re.findall(r'\[eaoui\]\[eaoui\]',word)) tripple \= len(re.findall(r'\[eaoui\]\[eaoui\]\[eaoui\]',word)) disc+=doubleAndtripple + tripple numVowels \= len(re.findall(r'\[eaoui\]',word)) if word\[:2\] \== "mc" : syls+=1 if word\[\-1:\] \== "y" and word\[\-2\] not in "aeoui" : syls +=1 for i,j in enumerate(word) : if j \== "y" : if (i != 0) and (i != len(word)\-1) : if word\[i\-1\] not in "aeoui" and word\[i+1\] not in "aeoui" : syls+=1 if word\[:3\] \== "tri" and word\[3\] in "aeoui" : syls+=1 if word\[:2\] \== "bi" and word\[2\] in "aeoui" : syls+=1 if word\[\-3:\] \== "ian" : if word\[\-4:\] \== "cian" or word\[\-4:\] \== "tian" : pass else : syls+=1 if word\[:2\] \== "co" and word\[2\] in 'eaoui' : if word\[:4\] in co\_two or word\[:5\] in co\_two or word\[:6\] in co\_two : syls+=1 elif word\[:4\] in co\_one or word\[:5\] in co\_one or word\[:6\] in co\_one : pass else : syls+=1 if word\[:3\] \== "pre" and word\[3\] in 'eaoui' : if word\[:6\] in pre\_one : pass else : syls+=1 negative \= \["doesn't", "isn't", "shouldn't", "couldn't","wouldn't"\] if word\[\-3:\] \== "n't" : if word in negative : syls+=1 else : pass if word in exception\_del : disc+=1 if word in exception\_add : syls+=1 return numVowels \- disc + syls 
```

This seemed like a lot just to count a few syllables. It made poor use of memory, too, by doing things like allocating variables that it then used one time. "Python programmers shouldn't worry about things like efficiency and memory usage"--but I do. I knew I could do better, and so I did.

### The Refactored Syllable Counter

```
 1 2 3 4 5 6 7 8 9 10 11 12 13 14 15 16 17 18 19 20 21 22 23 24 25 26 27 28 29 30 31 32 33 34 35 36 37 38 39 40 41 42 43 44 45 46 47 48 49 50 51 52 53 54 55 56 57 58 59 60 61 62 63 64 65 66 67 68 69 70 71 72 73 74 75 76 77 78 79 80 81 82 83 84 85 86 87 88 89 90 91 92 93 94 95 96 97 98 99 100 101
```

```
 def MySyllableCount(word): word \= word.lower() syls \= 0 disc \= 0 if len(word) <= 3 : return 1 double\_vowel \= len(findall(r'\[eaoui\]\[eaoui\]',word)) if word\[\-2:\] in \["es", "ed"\]: if double\_vowel \> 1 or len(findall(r'\[eaoui\]\[^eaoui\]',word)) \> 1 : if word\[\-3:\] in \["ted", "tes", "ses", "ied", "ies"\]: pass else: disc+=1 if word\[\-1:\] \== "e" : if word\[\-2:\] \== "le" and word not in \['whole','mobile','pole','male','female','hale','pale','tale','sale','aisle','whale','while'\]: pass else : disc+=1 disc += double\_vowel + len(findall(r'\[eaoui\]\[eaoui\]\[eaoui\]',word)) numVowels \= len(findall(r'\[eaoui\]',word)) if word\[:2\] \== "mc" : syls+=1 if word\[\-1:\] \== "y" and word\[\-2\] not in "aeoui" : syls +=1 for i,j in enumerate(word) : if j \== "y" : if (i != 0) and (i != len(word)\-1) : if word\[i\-1\] not in "aeoui" and word\[i+1\] not in "aeoui" : syls+=1 if word\[:3\] \== "tri" and word\[3\] in "aeoui" : syls+=1 if word\[:2\] \== "bi" and word\[2\] in "aeoui" : syls+=1 if word\[\-3:\] \== "ian" : if word\[\-4:\] in \["cian", "tian"\]: pass else : syls+=1 if word\[:2\] \== "co" and word\[2\] in 'eaoui' : if (set(\['coapt','coed','coinci'\]).intersection(\[word\[:4\], word\[:5\], word\[:6\]\])): syls+=1 elif (set(\['cool','coach','coat','coal','count','coin','coarse','coup','coif','cook','coign','coiffe','coof','court'\]).intersection(\[word\[:4\], word\[:5\], word\[:6\]\])): pass else : syls+=1 if word\[:3\] \== "pre" and word\[3\] in 'eaoui' : if word\[:6\] in \['preach'\]: pass else : syls+=1 if word\[\-3:\] \== "n't" : if word in \["doesn't", "isn't", "shouldn't", "couldn't","wouldn't"\]: syls+=1 else: pass if word in \['fortunately','unfortunately'\]: disc+=1 if word in \['serious','crucial'\]: syls+=1 return numVowels \- disc + syls 
```

Take comments and whitespace out, and Emre's counter comes in at 70 lines long. My version sits at 66 lines but cuts runtime by 9%. It pays to worry about things like efficiency and memory usage after all. As I marveled at my own brilliance, though, I realized that this might not matter. Emre gave this a shot back in 2016 with no guarantee of its accuracy. Cutting runtime by any number meant nothing if the algorithm did not work. Before I spent any more time trimming an unproven script, I needed to test it against a known good source; I needed to test it against a dictionary.

This seemed like an easy task:

1.  Read a word from the dictionary
2.  Use the algorithm to count its syllables
3.  Compare the algorithm's count to the dictionary's

As long as the algorithm gave me the right syllable count most of the time, I could speed it up, make it more accurate, and then repeat that process as many times as I wanted. I ran into problems starting with step one, though: UNIX has no native dictionary. It does have a wordlist, with over 200,000 words, but I needed a dictionary to give me valid words \*and\* the number of syllables they contained. Without that number, from an authoritative source, I had nothing to test the algorithm's accuracy.

Because I needed my script to pull words and syllable counts from the dictionary, I needed something with a command line interface. The built-in dictionary app on my Mac, `dictionary.app`, seemed like an easy answer, but supports only \[basic programatic access\](https://ift.tt/337yZ2w). `dictd` looked like it fit the bill, but I had trouble getting it to install. It "succeeded", but never ran. A third-party dictionary violated my self-reliance principle anyway, so I cleared all the install files and went back to my old standby: web scraping.

My script started out simple. Read words from the UNIX wordlist at `/usr/share/dict/words`, get a syllable breakdown from Google or [HowManySyllables.com](https://howmanysyllables.com), and record the result in a new wordlist. Check out my first try below.

### Syllable Dictionary Builder, version 1

```
 1 2 3 4 5 6 7 8 9 10 11 12 13 14 15 16 17 18 19 20 21 22 23 24 25 26 27 28 29 30 31 32 33 34 35 36 37 38 39 40 41 42 43 44 45 46 47 48 49 50 51 52 53 54 55 56 57 58 59 60 61 62 63 64 65 66 67 68 69 70 71 72 73 74 75 76 77 78 79 80 81 82 83 84 85
```

```
\# Method: BuildSyllableDictionary \# Purpose: Enrich wordlist with true syllables from a dictionary \# Parameters: none. def BuildSyllableDictionary(): \# Create a new instance of the web scraper s = Scraper() \# Open the wordlist s\_fd = open("/usr/share/dict/words", "r") \# Create the syllable dictionary file if it does not exist. if (not exists("./syllable\_dictionary.txt")): open("./syllable\_dictionary.txt", "w").close() \# Open the syllable dictionary c\_fd = open("./syllable\_dictionary.txt", "r") \# Clear and open a temporary output syllable dictionary, to write to. open("./syllable\_dictionary.txt.bak", "w").close() d\_fd = open("./syllable\_dictionary.txt.bak", "a") \# Enumerate the wordlist for i, word in enumerate(s\_fd): \# Convert wordlist word to lowercase and strip newline word = word.lower().strip() \# Read a line from the syllable dictionary comp = c\_fd.readline().split(",")\[0\].strip() \# If the word in the wordlist has already been added to the syllable \# dictionary, skip it. if (word == comp): continue \# Query Google for the definition of the wordlist's word. Depending on \# the user agent string, the number of syllables may be in a span or \# div. If neither element is in the response, try another source. resp = s.scrape("https://google.com/search?q=define%20"+word) if ('' in resp): resp = resp.split('',1)\[1\].split("",1)\[0\] print(word,",",resp.count("·")+1) d\_fd.write(word+","+str(resp.count("·")+1)+'\\n') continue elif ('

' in resp): resp = resp.split('

',1)\[1\].split(">",1)\[1\].split("<",1)\[0\] print(word,",",resp.count("·")+1) d\_fd.write(word+","+str(resp.count("·")+1)+'\\n') continue else: resp = "" \# If Google does not have a syllable breakdown for the target word, \# try HowManySyllables.com. if (resp == ""): resp = s.scrape("https://www.howmanysyllables.com/words/"+word) \# If the response contains a certain paragraph, parse the number of \# syllables. If not all has failed, so return -1 for the syllable count if ('

' in resp and '' in resp.split('

',1)\[1\]): resp = resp.split('

',1)\[1\].split('',1)\[1\].split('',1)\[0\] print(word,",",resp.count("-")+1) d\_fd.write(word+","+str(resp.count("-")+1)+'\\n') else: print(word,",",-1) d\_fd.write(word+","+str(-1)+'\\n') \# Close all files s\_fd.close() d\_fd.close() c\_fd.close() \# Append the temporary syllable dictionary to the actual \# syllable dictionary, then remove the temp file. s\_fd = open("./syllable\_dictionary.txt.bak", "r") d\_fd = open("./syllable\_dictionary.txt", "a") for i,line in enumerate(s\_fd): d\_fd.write(line) \# Close files s\_fd.close() d\_fd.close() \# Cleanup remove("./syllable\_dictionary.txt.bak") del s 
```

It took almost two days to get through A and B, at just over 25,000 words. I did not have the patience to spend a month working through the other 90% of the dataset, so I made some changes for B to Z.

First, I split up the 235,886 line wordlist by letter. This gave me twenty-six sub-wordlists: `a.txt`, `b.txt`, and so on.

```
 1 2 3 4 5 6 7 8 9 10 11 12 13 14 15 16 17 18 19 20 21 22 23 24 25 26 27 28 29 30 31
```

```
\# Method: SplitUpWordlist \# Purpose: Break wordlist into sub-wordlists by letter of alphabet \# Parameters: none. def SplitUpWordlist(): \# Open the wordlist wordlist\_fd = open("/usr/share/dict/words", "r") \# Keep track of which letters have their own output file alphabet = \[\] \# Enumerate the wordlist. For each letter, create a new wordlist file in \# the form {letter}.txt, that contains all letters starting with {letter}. for i,line in enumerate(wordlist\_fd): \# Transform the wordlist's word line = line.strip().lower() \# If the script has not processed {letter} yet, create {letter}.txt \# and write all words starting with {letter} to it. if (line\[0\] not in alphabet): try: d\_fd.close() except: pass open("./"+line\[0\]+".txt", "w").close() d\_fd = open("./"+line\[0\]+".txt", "a") d\_fd.write(line+'\\n') else: d\_fd.write(line+'\\n') \# Close the file wordlist\_fd.close() 
```

It would have taken me another twenty-six days to work through those twenty-six wordlists, so I decided to put my quad core processor to work by enabling multiprocessing. Python's handy `multiprocessing` module would farm out each dictionary lookup to its own core, which would allow me to use all eight of my logical processors to make quick work of this task. `BuildSyllableDictionaryWithMultiprocessing` farmed a sub-wordlist out to each processor. `BuildDictionary` enumerated the sub-wordlist to build the syllable dictionary. `DownloadSyllable` did the web scraping to capture the syllable count.

```
 1 2 3 4 5 6 7 8 9 10 11 12 13 14 15 16 17 18 19 20 21 22 23 24 25 26 27 28 29 30 31 32 33 34 35 36 37 38 39 40 41 42 43 44 45 46 47 48 49 50 51 52 53 54 55 56 57 58 59 60 61 62 63 64 65 66 67 68 69 70 71 72 73 74 75 76 77 78 79 80 81 82 83 84 85 86 87 88 89 90 91 92 93 94 95 96 97 98 99 100 101 102 103 104
```

```
\# Method: BuildSyllableDictionaryWithMultiprocessing \# Purpose: Enrich wordlist with syllables from dictionary, with multiprocessing \# Parameters: none. def BuildSyllableDictionaryWithMultiprocessing(): \# Find all source files of the form {letter}.txt files = \[x for x in listdir("./") if len(x) == 5\] \# Use multithreading to speed up capturing syllables for entire dictionary with Pool() as pool: pool.map(BuildDictionary, files) \# Method: BuildDictionary \# Purpose: Capture syllables for all words in a wordlist \# Parameters: \# - tgt: Source wordlist (String) def BuildDictionary(tgt): \# Clear an interim output file, then open for appending open("./interim\_" + tgt, "w").close() d\_fd = open("./interim\_" + tgt, "a") \# Open the source wordlist s\_fd = open("./" + tgt, "r") \# Open the existing syllable dictionary c\_fd = open("./syllable\_" + tgt, "r") \# Enumerate the wordlist.  for i,word in enumerate(s\_fd): \# Convert wordlist word to lowercase and strip newline word = word.lower().strip() \# Read a line from the syllable dictionary comp = c\_fd.readline().split(",")\[0\].lower().strip() \# If the word in the wordlist has already been added to the syllable \# dictionary, skip it. if (comp == word): continue \# If the word has not been added to the syllable dictionary, capture \# the syllable count and append the word and that number to the dict. d\_fd.write(line + "," + str(DownloadSyllable(line)) + '\\n') \# Close all files d\_fd.close() s\_fd.close() c\_fd.close() \# Append the temporary syllable dictionary to the actual \# syllable dictionary, then remove the temp file. s\_fd = open("./interim\_" + tgt, "r") d\_fd = open("./" + tgt, "a") for i,line in enumerate(s\_fd): d\_fd.write(line) \# Close files d\_fd.close() s\_fd.close() \# Delete temp file remove("./interim\_"+tgt) \# Method: DownloadSyllable \# Purpose: Capture syllables for single word \# Parameters: \# - word: Target word (String) def DownloadSyllable(word): \# Create a new instance of the Scraper class. This is necessary since these \# queries will be split up among multiple processors with dissimilar memory s = Scraper() \# Query Google for the definition of the wordlist's word. Depending on \# the user agent string, the number of syllables may be in a span or \# div. If neither element is in the response, try another source. resp = scrape("https://google.com/search?q=define%20"+word) if ('' in resp): resp = resp.split('',1)\[1\].split("",1)\[0\] print(word,",",resp.count("·")+1) return resp.count("·")+1 elif ('

' in resp): resp = resp.split('

',1)\[1\].split(">",1)\[1\].split("<",1)\[0\] print(word,",",resp.count("·")+1) return resp.count("·")+1 else: resp = "" \# If Google does not have a syllable breakdown for the target word, \# try HowManySyllables.com. if (resp == ""): resp = scrape("https://www.howmanysyllables.com/words/"+word) \# If the response contains a certain paragraph, parse the number of \# syllables. If not all has failed, so return -1 for the syllable count if ('

' in resp and '' in resp.split('

',1)\[1\]): resp = resp.split('

',1)\[1\].split('',1)\[1\].split('',1)\[0\] print(word,",",resp.count("-")+1) return resp.count("-")+1 else: print(word,",",-1) return -1 \# Cleanup del s 
```

Within a few minutes, Google blocked me. I gave cloud infrastructure a try, but Google just kept blocking my DoS scraper after about 300 connections. I had to write a new method to recover from these failures.

```
 1 2 3 4 5 6 7 8 9 10 11 12 13 14 15 16 17 18 19 20
```

```
\# Method: RecoverFromError \# Purpose: Append contents of partial temp files to syllable dictionaries. \# Parameters: none. def RecoverFromError(): \# Find all temp source files files = \[x for x in listdir("./") if ".txt" in x and "interim" in x\] \# Append cotnents of partial temp files to syllable dictionary for tgt in files: \# Open the files s\_fd = open("./"+tgt, "r") d\_fd = open("./"+tgt.replace("interim", "syllable"), "a+") \# Do the copying for i,line in enumerate(s\_fd): d\_fd.write(line) \# Close the files d\_fd.close() s\_fd.close() 
```

How Many Syllables never did block me, so I just commented out the part that checked Google first and drove on. Within a day, I had syllable count for all twenty-six sub-wordlists. `FinalCheck` made sure each sub-wordlist was not missing any words, `CombineWordlists` produced a master syllable dictionary I named `webS`, and `CompareWordlists` made sure the syllable dictionary had all the words from the original wordlist.

```
 1 2 3 4 5 6 7 8 9 10 11 12 13 14 15 16 17 18 19 20 21 22 23 24 25 26 27 28 29 30 31 32 33 34 35 36 37 38 39 40 41 42 43 44 45 46 47 48 49 50 51 52 53 54 55 56 57 58 59 60 61 62 63 64 65 66 67 68 69 70 71 72 73 74 75 76 77 78 79 80 81 82 83 84 85 86 87 88 89 90 91 92 93 94 95 96
```

```
\# Method: FinalCheck \# Purpose: Compare wordlists to syllable dictionaries \# Parameters: none. def FinalCheck(): \# Find all source wordlists of the form {letter}.txt files = sorted(\[x for x in listdir("./") if ".txt" in x and len(x) == 5\]) \# Compare each wordlist to its syllable dictionary, to make sure syllable \# dictionary has all words from the source wordlist. for tgt in files: \# Open the source wordlist and attempt to open syllable dictionary. \# If the dictionary does not yet exist, notify the user. source\_fd = open("./"+tgt, "r") if (not exists("./syllable\_"+tgt)): print("File '%s' does not exist." % ("./syllable\_"+tgt)) continue \# Open the syllable dictionary sylls\_fd = open("./syllable\_"+tgt, "r") \# Instantiate boolean to track similarity notTheSame = False \# Enumerate the wordlist. for i,source\_line in enumerate(source\_fd): \# Read a line from the source wordlist and the syllable dictionary source\_line = source\_line.strip().lower() sylls\_line = sylls\_fd.readline().split(",")\[0\].strip().lower() \# If the lines do not match, notify the user and set the boolean. if (source\_line != sylls\_line): print("Source line %d, '%s', and syllable dictionary line, '%s', do not match." % (i, source\_line, sylls\_line)) notTheSame = True \# Close all files source\_fd.close() sylls\_fd.close() \# Tell the user whether the syllable dictionary has all the words from \# the wordlist or if they diverge. if (notTheSame): print(tgt,"and","./syllable\_"+tgt+" are not the same.") else: print(tgt,"and","./syllable\_"+tgt+" ARE the same.") \# Method: CombineWordlists \# Purpose: Combine disparate sub-wordlists into a single wordlist. \# Parameters: \# - name: Filename for the monolithic wordlist (String) def CombineWordlists(name): \# Find all sub-wordlists like syllable\_{letter}.txt. Sort alphabetically. files = sorted(\[x for x in listdir("./") if "syllable\_" in x and ".txt" in x\]) \# Clear the master wordlist, then open for appending sub-wordlists open("./"+name, "w").close() master\_fd = open("./"+name, "a") \# Open each wordlist and write its contents to the master wordlist. for sub\_wordlist in files: sub\_fd = open("./"+sub\_wordlist, "r") for i,line in enumerate(sub\_fd): master\_fd.write(line) \# Close file sub\_fd.close() \# Close file master\_fd.close() \# Method: CompareWordlists \# Purpose: Compare master wordlist with syllable dictionary. \# Parameters: \# - master: File path for the master wordlist (String) \# - syl: File path for the syllable dictionary (String) def CompareWordlists(master, syl): \# Open the wordlists master\_fd = open(master, "r") syl\_fd = open(syl, "r") \# Enumerate the master wordlist for i,master\_line in enumerate(master\_fd): \# Read a line from the syllable dictionary syl\_line = syl\_fd.readline() \# Transform the lines for comparison master\_line = master\_line.lower().strip() syl\_line = syl\_line.split(",")\[0\].strip() \# Compare the two lines if (master\_line != syl\_line): \# Print the line number and the different words print("Line %d: master '%s' vs syllable dictionary '%s'" % (i, master\_line, syl\_line)) \# Exit so we can fix this line, then re-run break \# Close files master\_fd.close() syl\_fd.close() 
```

So how did my web scraper do? `FindNoSyllables`\--below--told me that out of 235,886 words in the wordlist, the scraper could not find syllables for 102,461. Not great.

```
 1 2 3 4 5 6 7 8 9 10 11 12 13 14 15 16 17 18 19 20 21 22 23 24 25 26 27
```

```
\# Method: FindNoSyllables \# Purpose: Find the words for which the dictionary does not count syllables \# Parameters: none. def FindNoSyllables(): \# Open the syllable wordlist s\_fd = open("./webS", "r") \# Keep track of the number of words without syllable counts count = 0 \# Enumerate the wordlist. for i,line in enumerate(s\_fd): \# Get the word and it's syllable count line = line.split(",") word = line\[0\].strip() sylls = int(line\[1\]) \# If the word has no syllable count, notify user and update total if (sylls == -1): print(word) count += 1 \# Close file s\_fd.close() \# Print count for user print(count,"records found.") 
```

A cursory look through that list, though, revealed that many appeared to be proper nouns. I checked with a new method, creatively named `FindNoSyllablesAndNotProperNouns`.

```
 1 2 3 4 5 6 7 8 9 10 11 12 13 14 15 16 17 18 19 20 21 22 23 24 25 26 27 28 29 30 31 32 33 34
```

```
\# Method: FindNoSyllablesAndNotProperNouns \# Purpose: Find words without syllable counts, that aren't proper nouns \# Parameters: none. def FindNoSyllablesAndNotProperNouns(): \# Open the syllable wordlist, and the master wordlist s\_fd = open("./webS", "r") w\_fd = open("/usr/share/dict/words", "r") \# Keep track of the number of words without syllable counts that are \# not proper nouns. count = 0 \# Enumerate the wordlist. for i,line in enumerate(s\_fd): \# Get the word and it's syllable count line = line.split(",") word = line\[0\].strip() sylls = int(line\[1\]) \# Get the word from the master wordlist m\_word = w\_fd.readline().strip() \# If the word has no syllable count, see if it's a proper noun if (sylls == -1): if (not m\_word\[0\].isupper()): print(word) count += 1 \# Close files s\_fd.close() w\_fd.close() \# Print count for user print(count,"records found.") 
```

85,524 left. Just by checking for proper nouns alone, I ruled out 16,937 words that, of course, will not be in a dictionary. What about the rest? Many are words with prefixes and suffixes whose roots exist in the dictionary, but that do not exist in their present form. Take "absenteeship", for example. Others are foreign words like "haori", which is a traditional Japanese jacket. "Pharyngotonsillitis" is a medical condition. Are these words? Yes. Am I concerned about testing my syllable counter against them? No. Whether it counts seven syllables in pharyngotonsillitis or not, I will sleep just fine at night.

  

As most projects do, this one started small--and then it got out of hand. [Proofer](https://zacs.site/projects.html#proofer) has not gotten any faster, but now I have a syllable dictionary to test the syllable count method so that I can then write a new method optimized for speed and memory use. Maybe, at the end of all this, Proofer will be a bit faster. That's ... something. Right?

For those of you who stuck around, you can download the syllable dictionary [here](https://gist.github.com/zacjszewczyk/b47c2307ca3d5a36c45f240cac54ea3d).

  
  
from Hacker News https://ift.tt/2LOOwyx