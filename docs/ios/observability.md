#Crashlytics

Client app needs to integrate crashlytics in his main application. If there is any crash happened then they need to send us the logs.
below are the steps to integrate firebase crashlytics pods into iOS project - 

###Install the dependency
```
pod 'Firebase/Crashlytics'
```

###Next, configure the Firebase module:
Import the Firebase module in your App struct or UIApplicationDelegate:

Swift
```swift
import Firebase
```
Objective C
```objc
@import Firebase;
```
Configure a FirebaseApp shared instance, typically in your App's initializer or your app delegate's application(_:didFinishLaunchingWithOptions:) method:

Swift
```swift
FirebaseApp.configure()
```
Objective C
```objc
[FIRApp configure];
```
### Set up Xcode to automatically upload dSYM files
To generate human readable crash reports, Crashlytics needs your project's debug symbol (dSYM) files. The following steps describe how to configure Xcode to automatically produce your dSYMs, process them, and upload the files whenever you build your app.

Open your project's Xcode workspace, then select its project file in the left navigator.
From the TARGETS list, select your main build target.
Click the Build Settings tab, then complete the following steps so that Xcode produces dSYMs for your builds.

Click All, then search for debug information format.
Set Debug Information Format to DWARF with dSYM File for all your build types.
Click the Build Phases tab, then complete the following steps so that Xcode can process your dSYMs and upload the files.

Click add > New Run Script Phase.

Make sure this new Run Script phase is your project's last build phase; otherwise, Crashlytics can't properly process dSYMs.
Expand the new Run Script section.

Note: For the remaining substeps, copy-and-paste the paths exactly as specified, and Xcode will resolve them. However, if you have issues with Xcode resolving these paths or a unique project structure, you can manually specify the paths instead.
In the script field (located under the Shell label), add the following run script.

This script processes your project's dSYM files and uploads the files to Crashlytics.
```
"${PODS_ROOT}/FirebaseCrashlytics/run"
```
In the Input Files section, add the paths for the locations of the following files:

The location of your project's dSYM files:
```
${DWARF_DSYM_FOLDER_PATH}/${DWARF_DSYM_FILE_NAME}/Contents/Resources/DWARF/${TARGET_NAME}
```
Providing the location of your project's dSYM files enables Crashlytics to process dSYMs for large apps more quickly.

The location of your project's built Info.plist file:
```
$(SRCROOT)/$(BUILT_PRODUCTS_DIR)/$(INFOPLIST_PATH)
```
Providing the location of your project's built Info.plist file enables Crashlytics to associate an app version with the dSYMs.
