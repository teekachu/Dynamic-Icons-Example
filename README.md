# Dynamic-Icons-Example
Topic - How to change your app icons programmatically
 
Intro: App icons are the first point of engagement for your users, an effective tool to catch their attention, and keep them away from exploring other potential options. Having alternative icon options is a great way to bring some personality to your app, and it’s also fairly simple to set up. 

Pre requisites: The ability to change app icons has been present since iOS 10.3, so please make sure you have a recent build of Xcode.

To get started, you will first need some icons. I like to use Figma to design mine, and there is an extension called “App Icon Toolkit” which exports your icon with the correct sizes as well as naming convention. How convenient!
<https://www.figma.com/community/file/824894885635013369>

Body: 
In Xcode, I have created a new group called “AlternativeIcons” to organize my icons. Each icon image should be available in both 2x (120 x120) and 3x (180 x 180) sizes, 1x size is optional. Please ensure to use the @2x and @3x naming convention that will allow iOS to automatically select the correct icon with the best resolution for the user’s device. 

<img one>

*** Note: Please ensure that these icons do not go inside the Asset catalogue. 

Next, we are going to create another Swift file called IconManager. In this file, we will create a class called IconManager that will contain three things - a constant, an enum, and a function. 

``` 
hello world
```
