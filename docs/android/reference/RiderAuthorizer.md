The following functions are exposed in the PopupCore class:

1.  Registering for email-password login based users. This creates a new user, and this user must login using email and password.

    ```java
    public static void registerWithEmailAndPassword(String email, String password, String firstName, String lastName, String phone, String data, long cityId)
    ```

2.  Registering for otp login based users. This creates a new user, and this user must login using OTP based authentication. Note that this is similar to the previous method, but does not accept a password field.

    ```java
    public static void registerWithPhoneNumber(final String email, final String socialId, String firstName, String lastName, String phone, String data, long cityId)
    ```

3.  Used to log in a user who was registered using `registerWithEmailAndPassword`.
    Returns a RiderInterface object if the login was successful.

    ```java
    public static RiderInterface loginWithPassword(String email, String password)
    ```

4.  Request an OTP. Returns an observable that emits a temporary token.
    This temporary token must be passed while trying to validate the OTP.

    ```java
    public static Observable<String> requestOtp(String phoneNumber)
    ```

5.  Verify an OTP. The token required here is the one generated in `requestOtp`.
    Returns a boolean indicating whether the verification was successful.
    The token parameter is the token received while requesting the OTP, and the code parameter is the OTP received.

    ```java
    public static Observable<Boolean> verifyPhoneNumber(String token, String code)
    ```

6.  Request an OTP. Returns an observable that emits the token required to validate the number.
    Also ensures that the phone number is associated with an existing user.
    Should be used in places where the user is required to be created, for example, during log in.

    ```java
    public static Observable<String> requestOtpForExistingUser(String phoneNumber, String SdkKey)
    ```

7.  Logging in with otp. The token parameter is the token received while requesting the OTP, and the code parameter is the OTP received.
    Requires `PopupAppManager` to have been initialized with a valid SDK key before this.

    ```java
    public static RiderInterface loginWithOtp(String phoneNumber, String token, String code)
    ```

8.  Restores user data from the shared preferences if it exists. This data is saved by default after login.
    Can be used to check if a user is already logged in at launch, and can avoid having to log in again.

    ```java
    public static RiderInterface restoreData()
    ```