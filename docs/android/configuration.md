## Configurations

The configurations for the app are set using the `PopupConfig` object.

The following constructors are available for `PopupConfig`:

```java
PopupConfig(String sdkKey)
PopupConfig(String sdkKey, boolean isFireBaseCrashlyticsEnabled)
PopupConfig(String sdkKey, List<Timber.Tree> loggers)
PopupConfig(String sdkKey, List<Timber.Tree> loggers, boolean isFireBaseCrashlyticsEnabled)
```

The following configuration items are available in the `PopupConfig` as well, each with their own getter and setter:

1. `loginMethod`: An enum, set to either `OTP` for registration and login using phone numbers, or `PASSWORD` for registration and login using an email and password. Set to `PASSWORD` by default.

2. `showPromocodes`: A boolean that controls whether or not the option to enter promo codes is shown. Set to `false` by default. This is required only if you want selected to follow promocodes model for discounting during onboarding. 

3. `showCampaigns`: A boolean that controls whether or not to show the campaign in the menu. Set to `false` by default. This allows you to have a separate menu item when user expands left hamburger menu. Clicking on this menu item will show additional details about your company and the campaign it is running currently. The information shown is set during onboarding.
