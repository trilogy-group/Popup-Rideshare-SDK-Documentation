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
init(Application application, @NonNull PopupConfig popupConfig)
```

The following functions are exposed in the PopupCore class:

1.  Registering for email-password login based users.

    ```java
    public static void registerWithEmailAndPassword(String email, String socialId, String password, String firstName, String lastName, String phone, String data, long cityId)
    ```

2.  Registering for otp login based users. Note that this is similar to the previous method, but does not accept a password field.

    ```java
    public static void registerWithPhoneNumber(final String email, final String socialId, String firstName, String lastName, String phone, String data, long cityId)
    ```

3.  Logging in with email and password.

    ```java
    public static RiderInterface loginWithPassword(String email, String password)
    ```

4.  Request an OTP. Returns an observable that emits the token required to validate the number.
    The token parameter is the token received, and the code parameter is the otp received.

    ```java
    public static Observable<String> requestOtp(String phoneNumber)
    ```

5.  Verify an OTP. The token required here is the one generated in `requestOtp`.
    Returns a boolean indicating whether the verification was successful.

    ```java
    public static Observable<Boolean> verifyPhoneNumber(String token, String code)
    ```

6.  Request an OTP. Returns an observable that emits the token required to validate the number.
    Also ensures that the phone number is associated with an existing user.
    Should be used in places where the user is required to be created, for example, during log in.
    Requires `PopupAppManager` to have been initialized with a valid SDK key before this.

    ```java
    public static Observable<String> requestOtpForExistingUser(String phoneNumber, String SdkKey)
    ```

7.  Logging in with otp. The token parameter is the token received, and the code parameter is the otp received.
    Requires `PopupAppManager` to have been initialized with a valid SDK key before this.

    ```java
    public static RiderInterface loginWithOtp(String phoneNumber, String token, String code)
    ```

8.  Restores user data from the shared preferences if it exists. This data is saved by default after login.

    ```java
    public static RiderInterface restoreData()
    ```

## RiderInterface Methods

The following methods are exposed in the RiderInterface, whic is received on successful login.

1.  Log out the current user

    ```java
    void logout()
    ```

2.  Check whether the user has accepted the terms.

    ```java
    boolean hasAcceptedTerms()
    ```

3.  Check whether a user is logged in.

    ```java
    boolean isLoggedIn()
    ```

4.  Check whether the logged in user is currently in a ride.

    ```java
    boolean isInRide()
    ```

5.  Get the logged in user's active ride.

    ```java
    Ride getActiveRide()
    ```

6.  Check whether the a given ride can be requested. Checks whether the pickup location is in a valid area, the user is enabled, and has atleast one payment method.

    ```java
    boolean canRequestRide(RideRequest request)
    ```

7.  Request a ride.

    ```java
    Observable<Ride> requestRide(RideRequest request)
    ```

8.  Request a fare estimate.

    ```java
    Observable<FareEstimateResponse> requestEstimate(double startLatitude, double startLongitude, double endLatitude, double endLongitude, long cityId, boolean inSurgeArea)
    ```

9.  Get a list of the nearby drivers.

    ```java
    Observable<List<DriverLocation>> getNearestDrivers(double lat, double lng, long cityId)
    ```

10. Add a new payment method for the logged in user.

    ```java
    Observable<Payment> addNewPayment(final Card card);
    ```

11. Delete a payment method for a logged in user.

    ```java
    Observable<List<Payment>> deletePayment(long cardId);
    ```

12. Mark a payment method as the primary payment method.

    ```java
    Observable<List<Payment>> setCardPrimary(final Payment payment)
    ```

13. Update a payment method.

    ```java
    Observable<Void> updatePayment(final Payment payment, int month, int year)
    ```

14. Get the entire payment history for a logged in user.

    ```java
    Observable<PaymentHistoryResponse> getPaymentHistory()
    ```

15. Get a part of the users payment history, by defining the page size and page number.

    ```java
    Observable<PaymentHistoryResponse> getPaymentHistory(int page, int pageSize)
    ```

16. Check if the user has an unpaid ride.

    ```java
    boolean hasUnpaid()
    ```

17. Pay the unpaid balance.

    ```java
    Observable<Void> payUnpaidBalance()
    ```

18. Register the token with the popup server to receive notifications.

    ```java
    Observable<Object> sendNotificationTokenToPopupServer(final String token, final AvatarType avatarType)
    ```

19. Send an email to Popup support

    ```java
    Observable<Void> contactSupportMail(String message, long rideId, long cityId)

    Observable<Void> contactSupportMail(String message, long cityId)
    ```

20. Get available support topics by avatar type.

    ```java
    Observable<List<SupportTopic>> getSupportTopics(AvatarType avatarType)
    ```

21. Get chidlren of a support topic.

    ```java
    Observable<List<SupportTopic>> getSupportTopicsByParent(int parentTopicId)
    ```

22. Get a support form by topic ID.

    ```java
    Observable<SupportForm> getSupportFormByTopic(int topicId)
    ```

23. Send a support request.

    ```java
    Observable<Void> sendSupportMessage(SupportRequest request)
    ```

24. Contact support over a lost or found item.
    TODO: These params reflect SupportFieldViewModel. Should we expose that as well?

    ```java
    Observable<ServerMessage> contactPair(final long rideId, Map<String, String> params)
    ```

25. Post information about a lost item.

    ```java
    Observable<ServerMessage> postLostItem(@Query("rideId") final long rideId, @QueryMap Map<String, String> params)
    ```

26. Post information about a found item.

    ```java
    Observable<ServerMessage> postFoundItem(Map<String, RequestBody> params)
    ```

27. Update a user's details.

    ```java
    Observable<User> updateUser(User user)
    ```

28. Request an email to be sent in case of a forgotten password.
    If the email is valid, the user will receive an email with their new password.

    ```java
    Observable<Void> forgotPassword(String email)
    ```

29. Update the password for a user.

    ```java
    Observable<Void> setNewPassword(String email, String password)
    ```
