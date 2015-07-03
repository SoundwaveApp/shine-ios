#Shine iOS SDK#
This guide will walk you through adding Shine to your iOS application.

##Getting started##

To begin using Shine you will need to acquire your unique application key. Currently these applications keys are given out on an ad-hoc basis by Soundwave. Please contact Soundwave if you have not received your key or would like to enquire about receiving a key.

###Requirements###

Shine SDK requires iOS 7.1+


###Manual Installation###

Shine SDK needs to be installed manually.

 1. Download the latest shine from [BitBucket](https://bitbucket.org/david_lynch/shine-ios/)
 2. Drag Shine.framework into your Xcode project, ticking the “Copy items if needed” checkbox.

**Add Other Linker Flag**

 3. Select your Xcode project in the file navigator sidebar.
 4. Select your project, then it’s “Build Settings" Tab.
 5. Search for “Other Linker Flags”.
 6. Double click the “Other Linker Flags” row’s value area, on the right side. A pop-up should appear.
 7. Add “-ObjC” by pressing the + button if it is hasn’t already been added

![linker.png](https://bitbucket.org/repo/KLGaee/images/906851690-linker.png)


#Initializing Shine#

To begin using shine follow these steps:

*  Import Shine into your `AppDelegate` class 
```
#!objective-c

#import <Shine/Shine.h>
```

* Add the following to your method `willFinishLaunchingWithOptions`. At this point you will need to provide your unique application key which is available by contacting Soundwave.

```
#!objective-c

- (BOOL)application:(UIApplication *)application willFinishLaunchingWithOptions:(NSDictionary *)launchOptions {
    [Shine setDeveloperKey:@"<Your-Dev-Key"];
    return YES;
}
```

Once you have added this code, Shine will start capturing data once your app launches.


#User Registration#

You can capture user registration data by adding the following code to your app:

```
#!objective-c

...
//Create a new Shine user
SWUser *shineUser = SWUser.new;
shineUser.firstName = @"John";
shineUser.lastName = @"Smith";
shineUser.email = @"john.smith@soundwave.com";

//Register the user with Shine
[Shine registerUserDetails:shineUser];
...
```