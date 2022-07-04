# Integrate Low Level SDK

In this version, the core functionality is exposed, and can be used with custom UI.

## Adding the dependency

Using gradle, you can add the dependency to your project as so

```java
implementation "com.messageone:popup-android:$latest_version"
```

## Configurations

The configurations for the app are set using the `PopupConfig` object.

The following constructors are available for `PopupConfig`:

```java
PopupConfig(String sdkKey)
PopupConfig(String sdkKey, boolean isFireBaseCrashlyticsEnabled)
PopupConfig(String sdkKey, List<Timber.Tree> loggers)
```

The following configuration items are available in the `PopupConfig` as well, each with their own getter and setter:

1. `loginMethod`: An enum, set to either `OTP` for registration and login using phone numbers, or `PASSWORD` for registration and login using an email and password. Set to `PASSWORD` by default.

2. `showDriverRegistration`: A boolean, which shows an option to sign up as a driver in the menu if set to `true`. Set to `false` by default.

3. `riderRegistrationInfo`: A `RiderRegistrationInfo` object that can hold the email, first name, and last name of the user, to allow prefilling values during registration steps.

4. `isFireBaseCrashlyticsEnabled`: A boolean to either enable or disable FireBase Crashlytics. Set to `false` by default.

5. `showPromocodes`: A boolean that controls whether or not the option to enter promo codes is shown. Set to `false` by default.

6. `showCampaigns`: A boolean that controls whether or not to show the campaign in the menu. Set to `false` by default.

## Initializing the SDK

The SDK must be initialized by calling the following method in PopupManager:

```java
init(Application application, @NonNull PopupConfig popupConfig);
```

## Launching the SDK

The SDK can be launched by calling the following method in Popup:

```java
launch(Context context);
```

Note: The SDK must be initialized before trying to launch it.

Example code:

```java
PopupConfig popupConfig = new PopupConfig("YOUR_SDK_KEY");
popupConfig.setLoginMethod(PopupConfig.LoginMethod.PASSWORD);
popupConfig.setShowDriverRegistration(true);
popupConfig.setRiderRegistrationInfo(riderRegistrationInfo);
popupConfig.setFireBaseCrashlyticsEnabled(true);
popupConfig.setShowPromocodes(true);
popupConfig.setShowCampaigns(false);
PopupAppManager.init(getApplication(), popupConfig);
Popup.launch(this);
```
