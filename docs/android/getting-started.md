Perform the below steps in order to setup Popup in your app in the plug and play mode


## 1. Adding the dependency

Using gradle, you can add the dependency to your project as so

```java
implementation "com.messageone:popup-android:$latest_version"
```
Note that during development stage, you might want to use test environment. Check the [Faqs](./faq.md) regarding how to use test environment.

## 2. Create PopupConfig 
Create an instance of PopupConfig class, refer [Configuration](./configuration.md)

## 3. Initializing the SDK

The SDK must be initialized by calling the following method in PopupAppManager where Application is your [application](https://developer.android.com/reference/android/app/Activity#getApplication()):

```java
init(Application application, @NonNull PopupConfig popupConfig);
```

## 4. Launching the SDK

The SDK can be launched by calling the following method in Popup:

```java
launch(Context context);
```

Note: The SDK must be initialized before trying to launch it. You can initialise during start of your app too for a quicker launch experience.

Below example can be written in any of your activity class, triggered to be executed on click of some UI element:

```java
PopupConfig popupConfig = new PopupConfig("YOUR_SDK_KEY");
popupConfig.setLoginMethod(PopupConfig.LoginMethod.PASSWORD);
popupConfig.setFireBaseCrashlyticsEnabled(true);
popupConfig.setShowCampaigns(false);
PopupAppManager.init(getApplication(), popupConfig);
Popup.launch(this); 
```


## 5. Demo application
A demo application covering the steps above is available at github.


----

To use build and integrate mode, please refer the reference section of the documents.
We will be adding documentation and guides for this mode in future.
