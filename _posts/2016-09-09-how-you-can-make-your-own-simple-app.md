---
title: 'How You Can Make Your Own Simple App With VBA'
date: 2020-01-23T03:19:00+01:00
draft: false
---

![excel-cells-vba](https://static.makeuseof.com/wp-content/uploads/2018/03/excel-cells-vba.jpg)

Visual Basic for Applications (VBA) is a remarkable language. Built into Microsoft Excel, this language can be used to program apps right inside an Excel worksheet.

It’s easily accessible; you don’t need anything more than a working version of Microsoft Office. This makes it very easy to get started.

We’re going to walk through creating an Excel VBA application. It’s going to be simple but will cover some basics that you can use to build more complicated programs in Excel.

What Can I Do With VBA?
-----------------------

Certainly, there are other programming languages that are widely used to create software. VBA remains popular thanks to the widespread use of Excel and how easy it is to get going (you just need Excel to get started).

VBA can perform all kinds of tasks like [sending emails from an Excel spreadsheet](//www.makeuseof.com/tag/send-emails-excel-vba/) to [creating custom macro toolbars](//www.makeuseof.com/tag/custom-excel-toolbar-vba-macros/).

How to Make Your Own VBA Application
------------------------------------

The VBA application you’re going to make is a simple data entry style form that will take some input and make an output for you. You’ll write VBA code to do some processing to the input, just like programmed software.

The program is going to take a bunch of text and convert it into an HTML output file that can be copied into a blog.

If you want a rundown of the language before writing an app, consider a [beginner’s tutorial on writing VBA macros in Excel](//www.makeuseof.com/tag/vba-macros-excel-tutorial/). Let’s get started!

### Creating the Application Framework

First, choose an Office product installed on your PC. It can be Word, Excel, Powerpoint, Access or any other.

In this example, we will use Excel to create the application. VBA is widely used with Excel because of the added power it gives spreadsheets. To get started you’re going to need to create a button to trigger your code.

If you’re using Excel 2007 or later, you’ll find these controls on the menu under **Developer > Insert**. Find the **Command Button** control (under **ActiveX Controls**), and you’ll be ready to roll.

If you can’t see the menu option, here’s [how to add the Developer tab to Excel](//www.makeuseof.com/tag/developer-tab-ribbon-microsoft-word-excel/). This is pretty simple and you only need to do it once.

Click on it and draw a command button onto the spreadsheet. This button will launch your application.

Another approach would be to write a macro that automatically launches your script when you open the Excel file, but that’s a little more advanced. For now, let’s use a command button.

Make sure the **Design Mode** selection is on—in the picture above it’s the triangle/ruler/pencil icon. Double click on the command button you created and the VBA Project Editor will open.

This is the development area where you will create your new application. The first thing you want to do is make the front screen of your app. To do this, right-click on the project that’s already open. In this case, it’s called **VBAProject** which is the default. Then, select **Insert** and **UserForm**.

Your user form is now loaded into your project under the Forms folder with the default name of **UserForm1**.

Double click on **Sheet1**. This is where you write the code that will run when you click on the command button.

On the right panel, you should see the **CommandButton1** selected and **CommandButton1\_Click** code already there. This is called a function. VBA functions house VBA code. [Functions are critically important to programming languages](//www.makeuseof.com/tag/programming-languages-need-functions/) and VBA is no exception.

So, what do you want your command button to do when you click on it? You want it to load the User Form that you just created. You do this by typing in a single line, **Load UserForm1**.

Now that you have your program set up to launch the moment you click on the command button you created, it’s time to design the application.

To design the form, right-click on **UserForm1**, and select **View Object**. You’ll see the form show up on the right side of the screen. You can click on the form and drag the border to resize it however you like.

Using the Controls toolbox you can add text fields, labels, and command buttons to your form. These are the basic components of a  VBA application.

You’re going to create a basic layout using some text boxes, and labels.

With all forms the **Properties** box lets you adjust settings for the form. You want to edit the **Caption** field to something that makes sense. This name is how your program is going to reference that item, so choose something that’s clear and makes sense.

### Adding More Functionality

What you’ve already created would be more than enough for most applications. There are some basic buttons that make the text fields interact with the Excel spreadsheet.

Let’s take it up a notch. It’s time to create the part of the app which will output a file to your computer. You can read and write to files by adding what’s called a “Reference” to your project.

A reference is an “add-on” that allows you to write extra commands in your program.

You can usually find the list of references under **Tools** in the toolbar by selecting **References**. For I/O functionality, just scroll down and select **Microsoft Scripting Runtime**.

Now that the references are there, let’s create a new button. In the toolbar create a new Command Button by simply clicking on the icon. This button will generate the output when clicked.

Change the caption to **Create Output** so it’s easy to remember what the button does.

Double-clicking on that button, you’ll see the function for the button click event. Let’s add some code to run the output. This code may look complicated, but it’s really not bad once you break it down.

To set up file reading and writing once you’ve added the Reference, use this code:

```
Dim fso As New FileSystemObject  
Dim fnum  
Dim MyFile as String  
MyFile = "c:\\temp\\OutputArticle.txt"  
fnum = Freefile()
```

What does this do? Well, it sets up **MyFile** as the path to your output file you want to write to, and it creates **fnum** as the file identification key for the code.

Finally, you connect these two together by typing **Open MyFile For Output as fnum.** You’ve got your open connection to write to the file by issuing **Print #fnum** commands.

These **Print **commands will print the text you place after it. There is some basic HTML in some of these statements, some others you will notice are simply variables like **txt1stSection**.

These variables are linked to the text boxes you made in the UserForm.

### Printing Output

Head back to the form and fill in all the text fields on the main application screen.

Now switch back out of “Design” mode, click on the output button, and open the file to confirm the results.

Sure enough, there is the web code formatted with the required HTML tags defined in the program. All the text from those text fields is printed and ready to be copied into a blog.

With just these VBA basics you have a lot more you can create.

You could create a simple input form for data entry that outputs the data to either a CSV file. You could also write an application that reads information out of a text file, formats the information, and then loads that data into a spreadsheet.

Doing More With VBA
-------------------

The possibilities are really limited only by your own imagination when it comes to VBA. You don’t have to purchase an expensive development package like Visual Studio. Just open up any MS Office program, switch to the VBA Editor, and you can create apps.

To learn more about VBA there are some great [resources to learn Excel macros](//www.makeuseof.com/tag/excel-macros-resources/) and [tips to avoid some common mistakes writing Excel VBA code](//www.makeuseof.com/tag/4-mistakes-can-avoid-programming-excel-macros-vba/).

VBA is not just limited to Windows systems, [Mac users can write Excel VBA code](//www.makeuseof.com/tag/macros-excel-mac-save-time/) as well. There’s no better time than today to learn this established language.

Read the full article: [How You Can Make Your Own Simple App With VBA](https://www.makeuseof.com/tag/simple-app-vba/)

  
  
from MakeUseOf https://ift.tt/2RM1jn0  
via [IFTTT](https://ifttt.com/?ref=da&site=blogger)