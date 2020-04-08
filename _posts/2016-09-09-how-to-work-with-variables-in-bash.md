---
title: 'How to Work with Variables in Bash'
date: 2019-10-07T13:09:00+01:00
draft: false
---

![A Linux terminal with green text on a laptop.](https://www.howtogeek.com/wp-content/uploads/2019/04/img_5cc898db4e3d3.png)

[Fatmawati Achmad Zaenuri/Shutterstock](https://www.shutterstock.com/image-vector/command-line-interface-cli-programming-language-1278851809)

Variables are vital if you want to write scripts and understand what that code you’re about to cut and paste from the web will do to your Linux computer. We’ll get you started!

Variables 101
-------------

Variables are named symbols that represent either a string or numeric value. When you use them in commands and expressions, they are treated as if you had typed the value they hold instead of the name of the variable.

To create a variable, you just provide a name and value for it. Your variable names should be descriptive and remind you of the value they hold. A variable name cannot start with a number, nor can it contain spaces. It can, however, start with an underscore. Apart from that, you can use any mix of upper- and lowercase alphanumeric characters.

Examples
--------

Here, we’ll create five variables. The format is to type the name, the equals sign `=`, and the value. Note there isn’t a space before or after the equals sign. Giving a variable a value is often referred to as _assigning_ a value to the variable.

We’ll create four string variables and one numeric variable, `this_year:`

```
me=Dave
``````
my\_boost=Linux
``````
him=Popeye
``````
his\_boost=Spinach
``````
this\_year=2019
```

![Five variables in a terminal window.](https://www.howtogeek.com/wp-content/uploads/2019/09/1-13.png)

To [see the value](http://man7.org/linux/man-pages/man1/echo.1.html) held in a variable, use the `echo` command. You must precede the variable name with a dollar sign `$` whenever you reference the value it contains, as shown below:

```
echo $my\_name
``````
echo $my\_boost
``````
echo $this\_year
```

![The ](https://www.howtogeek.com/wp-content/uploads/2019/09/2-12.png)

Let’s use all of our variables at once:

```
echo "$my\_boost is to $me as $his\_boost is to $him (c) $this\_year"
```

### [Read the remaining 64 paragraphs](https://www.howtogeek.com/442332/how-to-work-with-variables-in-bash/)