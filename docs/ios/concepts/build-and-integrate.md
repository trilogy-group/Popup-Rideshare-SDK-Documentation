
This page assumes you have gone over the concepts mention in plug and play mode.
If you need to build your custom UI from scratch and only access Popup Sdk for the Ride hailing services, you will need to understand below concepts to interact with the system. We are yet to document tutorials for this mode but you can still head over to References and build your integration.

### RiderAuthorizer

####RWRiderRegisterAPIDelegate

Popup needs that each rider be registered with us with a valid email and phone number. The RWRiderRegisterAPIDelegate encapsulates operations that will allow you to register riders with us . Registration is also allowed in two different modes viz Password and OTP. An app has to select a mode before being released. Currently we do not support changing login modes once the app has released and users are registered.

####RWRiderLoginAPIDelegate

 The RWRiderLoginAPIDelegate encapsulates operations that will allow you to login riders with us .Login is also allowed in two different modes viz Password and OTP. An app has to select a mode before being released. Currently we do not support changing login modes once the app has released and users are registered.

### RWRiderClient
Successful login will give you access to instance of RWRiderClient. This class allows you to confirm that rider has accepted the terms, request a ride, setup payments, access trip history, check if he can request a ride, check if he is alreay in an active ride etc.
After successful login, all operations that a user can do, will be avaliable with RWRiderClient.
