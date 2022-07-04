The following methods are exposed in the AuthorizedRider, which is received on successful login.

1.  Log out the current user.

    ```java
    void logout()
    ```

2.  Check whether the user has accepted the Popup terms and conditions.

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

5.  Get the logged in user's active ride, if it exists.

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

10. Add a new payment credit card for the logged in user.

    ```java
    Observable<Payment> addNewPayment(final Card card);
    ```

11. Delete a credit card for a logged in user.

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

17. Pay off the balance for any unpaid ride.

    ```java
    Observable<Void> payUnpaidBalance()
    ```

18. Register the token with the popup server to receive notifications. This is automatically done during login, but must be also called when Firebase refreshed the token.

    ```java
    Observable<Object> sendNotificationTokenToPopupServer(final String token, final AvatarType avatarType)
    ```

19. Send an email to Popup support.

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

27. Update a user's details. Accepts the updated user object.

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