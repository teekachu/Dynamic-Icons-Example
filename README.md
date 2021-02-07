# Dynamic-Icons-Example
Topic - How to change your app icons programmatically
 
Intro: 
App icons are the first point of engagement for your users, an effective tool to catch their attention, and keep them away from exploring other potential options. Having alternative icon options is a great way to bring some personality to your app, and it’s also fairly simple to set up. 

Pre requisites: 
The ability to change app icons has been present since iOS 10.3, so please make sure you have a recent build of Xcode.

To get started, you will first need some icons. I like to use Figma to design mine, and there is an extension called “App Icon Toolkit” which exports your icon with the correct sizes as well as naming convention. How convenient!
<https://www.figma.com/community/file/824894885635013369>

Body: 
In Xcode, I have created a new group called “AlternativeIcons” to organize my icons. Each icon image should be available in both 2x (120 x120) and 3x (180 x 180) sizes, 1x size is optional. Please ensure to use the @2x and @3x naming convention that will allow iOS to automatically select the correct icon with the best resolution for the user’s device. 

<img one>

*** Note: Please ensure that these icons do not go inside the Asset catalogue. 

Next, we are going to create another Swift file called IconManager. In this file, we will create a class called IconManager that will contain three things - a constant, an enum, and a function. 

``` 
class IconManager {
    let application = UIApplication.shared
    
    // same naming convention in the plist to reference to actual files
    enum AppIcon: String {
        case charmanderIcon
        case pikachuIcon
    }
   
    func changeAppIcon(to appIcon: AppIcon) {
        application.setAlternateIconName(appIcon.rawValue)
    }
}
```

Next, go to the project navigator, right click on the Info.plist file, and choose open as Source Code. Yes, it does look kind of intimidating, but I promise it’s much less complex than it seems. 

Scroll to the bottom until you see
```
</dict>
</plist>
```

Directly before </dict>, please add this long and intimidating code. Just kidding! I will explain in a little bit:

```
 <key>CFBundleIcons</key>
    <dict>
        <key>CFBundlePrimaryIcon</key>
        <dict>
            <key>CFBundleIconFiles</key>
            <array>
                <string>58-1</string>
            </array>
            <key>UIPrerenderedIcon</key>
            <false/>
        </dict>
        <key>CFBundleAlternateIcons</key>
        <dict>
            <key>charmanderIcon</key>
            <dict>
                <key>CFBundleIconFiles</key>
                <array>
                    <string>charmander</string>
                </array>
                <key>UIPrerenderedIcon</key>
                <false/>
            </dict>
            <key>pikachuIcon</key>
            <dict>
                <key>CFBundleIconFiles</key>
                <array>
                    <string>pikachu</string>
                </array>
                <key>UIPrerenderedIcon</key>
                <false/>
            </dict>
        </dict>
    </dict>
```

The highlighted lines need to be updated in your own code, so let’s start from the top. The key CFBundlePrimaryIcon refers to your default icon, the key CFBundleIconFiles  refers to the file that contains your primary icon, and in between the two <string> tags should be the name of your primary icon. You can find this by going to your assets folder - AppIcons - find the 2x iPhone app icon  - right click -  select show in finder. Everything before .png should be the name of your image, excluding the 1x / 2x/ 3x naming convention. For example, my files are named 58-1@2x.png, so i would put 58-1 between the <string> tags. 

Moving on to CFBundleAlternateIcons.  In the example XML, I used the references charmanderIcon and pikachuIcon as keys because these are also the same as my cases in the IconManager.swift file. If you look inside of my changeAppIcon() function, I am setting the alternative icon names as the raw value of each case. As such, we have to use the same reference name inside our Info.plist file, so Xcode knows what to look for. Your file name inside AlternativeIcons group will go in between the <string> tags for the corresponding icon. 

The last thing we need to do is to add an action to the call-to-action buttons,  and this is only one line of code. Go to the ViewController where your buttons are located. 



