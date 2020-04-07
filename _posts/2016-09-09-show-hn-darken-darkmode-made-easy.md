---
title: 'Show HN: Darken – Darkmode Made Easy'
date: 2020-01-17T01:32:00+01:00
draft: false
---

[](https://github.com/ColinEspinas/darken#darken)darken
=======================================================

[![Codacy Badge](https://camo.githubusercontent.com/836854647a12516dbae96e3d17c432ea8c889134/68747470733a2f2f6170692e636f646163792e636f6d2f70726f6a6563742f62616467652f47726164652f6331313365356163666566363434333061653064623639313761373862363132)](https://app.codacy.com/manual/ColinEspinas/darken?utm_source=github.com&utm_medium=referral&utm_content=ColinEspinas/darken&utm_campaign=Badge_Grade_Dashboard) [![Issue Badge](https://camo.githubusercontent.com/de7da24406c2a3bd98c22c79c712628fdff8fe30/68747470733a2f2f696d672e736869656c64732e696f2f6769746875622f6973737565732f636f6c696e657370696e61732f6461726b656e)](https://github.com/ColinEspinas/darken/issues) [![Licence Badge](https://camo.githubusercontent.com/d9c88d17dce200072bae9e11d9454a45582b9de2/68747470733a2f2f696d672e736869656c64732e696f2f6769746875622f6c6963656e73652f636f6c696e657370696e61732f6461726b656e)](https://github.com/ColinEspinas/darken/blob/master/LICENSE) [![Demo badge](https://camo.githubusercontent.com/90b96c67285b7beabeb48f30f1e2de3ddfff82aa/68747470733a2f2f696d672e736869656c64732e696f2f62616467652f2d44656d6f253230417661696c61626c652d627269676874677265656e)](https://colinespinas.github.io/darken/)

🌑 Darkmode made easy

[](https://github.com/ColinEspinas/darken#table-of-contents)Table of Contents
-----------------------------------------------------------------------------

[](https://github.com/ColinEspinas/darken#getting-started)Getting Started
-------------------------------------------------------------------------

### [](https://github.com/ColinEspinas/darken#%EF%B8%8F-using-the-cdn)✈️ Using the CDN

Just use this snippet to include darken to your code:

```
<script src\="https://unpkg.com/darken"\>script> <script\>  const darkmode \= new darken(); script>
```

### [](https://github.com/ColinEspinas/darken#-using-npm)📦 Using NPM

Install darken with npm:

And import it in your code:

```
import darken from 'darken'; const darkmode \= new darken();
```

[](https://github.com/ColinEspinas/darken#usage)Usage
-----------------------------------------------------

### [](https://github.com/ColinEspinas/darken#basic)Basic

Here is a basic usage of darken:

```
 <button id\="darkmode-button"\>Toggle darkmodebutton> <script src\="path/to/darken"\>script> <script\>  const darkmode \= new darken({  class: "darkmode-active",  variables: {  "\--primary-color" : \["#000000", "#fafafa"\],  "\--background-color" : \["#fafafa", "#000000"\]  },  toggle: "#darkmode-button",  }); script>
```

You can either use a class and/or CSS variables to customize your styles.

[](https://github.com/ColinEspinas/darken#options)Options
---------------------------------------------------------

```
const defaultOptions \= { container: null, default: "light", toggle: null, class: "darken", variables: {}, }
```

### [](https://github.com/ColinEspinas/darken#container)container

_Type: `String`_, _Default: `null`_

Element selector to the container of darken. The darkmode will be applied only to the selected container.

If the value is left to \`\`null\`, the document element will be selected instead.

### [](https://github.com/ColinEspinas/darken#default)default

_Type: `String`_, _Default: `"light"`_

Defines the default mode on page load.

### [](https://github.com/ColinEspinas/darken#toggle)toggle

_Type: `String`_, _Default: `null`_

Element selector to the toggle button, the selected element will call the `toggle` method on click.

### [](https://github.com/ColinEspinas/darken#class)class

_Type: `String`_, _Default: `"darken"`_

Class that will be added to the selected container when the darkmode is active. The class is removed of the selected container once the darkmode is disabled.

If no container is selected, the class will be added to the `body` element instead.

### [](https://github.com/ColinEspinas/darken#variables)variables

_Type: `Object`_, _Default: `{}`_

List of CSS variables that will change when the darkmode is active.

The keys of the object are the variables names, the value are arrays where the 1th index is the value the variable will take in lightmode and the 2nd index the value the variable will take in darkmode.

```
variables: { "\--name-of-the-variable": \["lightmode value", "darkmode value"\], "\--background-color": \["white", "black"\], }
```

[](https://github.com/ColinEspinas/darken#api)API
-------------------------------------------------

The `darken` class is the entry point to the library.

```
const darkmode \= new darken(options);
```

### [](https://github.com/ColinEspinas/darken#toggle-1)toggle()

_Return: `none`_

Toggles darkmode.

### [](https://github.com/ColinEspinas/darken#on)on()

_Return: `none`_

Enables darkmode.

### [](https://github.com/ColinEspinas/darken#off)off()

_Return: `none`_

Disables darkmode.

[](https://github.com/ColinEspinas/darken#contributing)Contributing
-------------------------------------------------------------------

Any help and contribution is always welcome, feel free to submit issues and/or contribute to the project.

1.  Fork the Project
2.  Create your Feature or Fix Branch (`git checkout -b feature/feature-name` or `git checkout -b fix/fix-name`)
3.  Commit your Changes (`git commit -m 'Add some feature or fix'`)
4.  Push to the Branch (`git push origin feature/feature-name` or `git push origin fix/fix-name`)
5.  Open a Pull Request

[](https://github.com/ColinEspinas/darken#license)License
---------------------------------------------------------

darken is distributed under the MIT License. See `LICENSE` for more information.

[](https://github.com/ColinEspinas/darken#contact)Contact
---------------------------------------------------------

Colin Espinas - [Website](https://colinespinas.com) - [contact@colinespinas.com](mailto:contact@colinespinas.com)

Project link: [https://github.com/ColinEspinas/darken](https://github.com/ColinEspinas/darken)

[](https://github.com/ColinEspinas/darken#acknowledgements)Acknowledgements
---------------------------------------------------------------------------

  
  
from Hacker News https://github.com/ColinEspinas/darken