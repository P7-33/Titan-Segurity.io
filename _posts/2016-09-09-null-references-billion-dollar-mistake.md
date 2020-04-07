---
title: 'Null References: The Billion Dollar Mistake'
date: 2020-01-11T14:47:00+01:00
draft: false
---

![](https://res.infoq.com/presentations/Null-References-The-Billion-Dollar-Mistake-Tony-Hoare/en/mediumimage/tony-hoare-big.jpg "Null References: The Billion Dollar Mistake")  

Your message is awaiting moderation. Thank you for participating in the discussion.

In some ways, the existence of null, in a business context, has become a necessary evil given that all of the mainstream relational databases support the storage of null values. Consequently, programmers need to be able to represent these values in programming languages which interact with these databases.  
  
With that said, what makes null an expensive proposition, is not its existence or even that null pointer exceptions are thrown at runtime. What makes null an expensive proposition, is that it is an unchecked runtime exception. For example, in the context of Java, there are checked exceptions and unchecked exceptions. The compiler forces you to explicitly handle checked exceptions by throwing compilation errors when you don't handle them. Runtime exceptions, by contrast, hide in your code like figurative land mines, often without the programmer even realizing they are there, waiting for an unsuspecting user to step on them. To help mitigate this, I find myself beginning all of my methods with a series of utility function calls like this:  
  
Util.assertNotNull(arg1);  
  
This prevents some unintended behaviors by failing quickly when an unexpected null is encountered and makes it more likely that null pointer exceptions will be found during testing, prior to releasing the software to users. However, going back to the land mine analogy, the user's leg still gets blown off if they happen to step on one. This costs the user time and money and it costs the author time and money.  
  
It was mentioned in the talk that some newer languages have added the capability of declaring variables as being not null, which would be much more convenient way of doing what I'm already doing with my utility methods. However, by my way of thinking, this is backwards. I am of the view that all variables should be not-null by default and that you should be allowed to optionally declare variables as being nullable. I understand that they have to do it this way for backwards compatibility reasons with existing programs but, in an ideal world, this is backwards and only a marginal improvement over my utility method approach because the programmer still has opt-in for their variables to not be nullable. Convincing programmers to do "the right thing" is not unlike herding cats. When they need a variable, they are going to declare a variable in the quickest easiest way possible and, consequently, the majority of their variables are going to be nullable and their programs can be expected to behave in much the same was as programs written prior to the introduction of the not-null concept. I've seen this kind of phenomenon innumerable times, over the years. If a language designer wants a programmer to "do the right thing" you have to make it easy for them to do or you have to force them to do it. In this sense, I am in complete agreement that a language designer should assume responsibility for the errors made by the programmers utilizing their language.  
  
In my estimation, what would be a significant improvement would be to make all variables not-null by default. Then, when a programmer decides that they want to use a null reference, they can opt-in to using a nullable type as opposed to opting-out of nullable types in cases where they either do not need or want nullable types. You could then change null pointer exceptions from unchecked exceptions to checked exceptions so that, when you attempted to assign a nullable type to a non-nullable type, you could then emit a compiler error which forces the programmer to handle the potential for a null pointer exception with a standard try/catch block. For example:  
  
MyClass myClass1; // Compiler error - uninitialized value  
nullable MyClass myClass2; // No compiler error  
  
MyClass myClass1 = new MyClass(); // No compiler error  
nullable MyClass myClass2; // No compiler error  
  
myClass2 = myClass1; // No exception thrown under any circumstances  
myClass1 = myClass2; // Throws checked NullPointerException and emits a compiler error if not explicitly handled  
  
try {  
// Throws a checked null pointer exception if myClass2 contains null  
myClass1 = myClass2;  
}  
  
catch (NullPointerException e) {  
// handle error  
}  
  
While not a perfect solution, this would help push programmers toward explicitly handling null pointers and, thereby, I believe, significantly reduce the number of null pointer exceptions which are encountered in the wild.

  
  
from Hacker News https://ift.tt/2p49eSg