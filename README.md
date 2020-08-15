Getting started:

since this project contains yarn as dependency manager make sure you have yarn in your system. easy way to get with npm is: `npm i -g yarn`

Then enter the following commands to get it running in your ios-simulator and android-emulator.

Run instructions for iOS:

    • cd NotificationTester && npx react-native run-ios
    - or -
    • Open NotificationTester/ios/NotificationTester.xcworkspace in Xcode or run "xed -b ios"
    • Hit the Run button

Run instructions for Android:
• Have an Android emulator running (quickest way to get started), or a device connected.
• cd NotificationTester && npx react-native run-android

Run instructions for Windows and macOS:
• See https://aka.ms/ReactNative for the latest up-to-date instructions.

## Step 1:

### Create a new firebase project

- visit [Google Firebase Console](https://console.firebase.google.com/) and create one.

### add ios app in the newly created firebase project.

- we need to specify the bundle identifier, here I used `com.saileshkasaju.notificationtester`
- Download the config file `GoogleService-Info.plist`
- Move the GoogleService-Info.plist file you just downloaded into the root of your Xcode project and add it to all targets.
  ![setup instructions](https://www.gstatic.com/mobilesdk/160426_mobilesdk/images/xcode_project_panel@2x.png 'Instructions for Xcode')
- update the bundle identifier in the `General` tab of project in Xcode.

### add android app in the newly created firebase project.

- we need to specify the package name, here from `android/app/src/main/AndroidManifest.xml` in my case `com.notificationtester`
- Download the config file `google-services.json`
- Switch to the Project view in Android Studio to see your project root directory.
- Move the google-services.json file you just downloaded into your Android app module root directory.
  ![setup instructions](https://www.gstatic.com/mobilesdk/160426_mobilesdk/images/android_studio_project_panel@2x.png 'Instructions for Xcode')
- update the bundle identifier in the `General` tab of project in Xcode.

## Step 2:

#### Configure Firebase with iOS credentials

open `/ios/{projectName}/AppDelegate.m` file, and add the following to the top of the file:

```
#import <Firebase.h>
```

Within your existing didFinishLaunchingWithOptions method, add the following to the top of the method:

```
- (BOOL)application:(UIApplication *)application didFinishLaunchingWithOptions:(NSDictionary *)launchOptions {
  // Add me --- \/
  if ([FIRApp defaultApp] == nil) {
    [FIRApp configure];
  }
  // Add me --- /\
  // ...
}
```

Open your projects /ios/Podfile and add the globals shown below to the top of the file:

```
# Override Firebase SDK Version
$FirebaseSDKVersion = '6.13.0'
```

# Install & setup the app module

`yarn add @react-native-firebase/app`

# Install the messaging module

`yarn add @react-native-firebase/messaging`

`cd ios/ && pod install`
