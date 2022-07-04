
This page assumes you have gone over the concepts mention in plug and play mode.
If you need to build your custom UI from scratch and only access Popup Sdk for the Ride hailing services, you will need to understand below concepts to interact with the system. We are yet to document tutorials for this mode but you can still head over to References and build your integration.

### RiderAuthorizer
Popup needs that each rider be registered with us with a valid email and phone number. The  RiderAuthorizer encapsulates operations that will allow you to register riders with us as well as login them with the system. Registration is also allowed in two different modes viz Password and OTP. An app has to select a mode before being released. Currently we do not support changing login modes once the app has released and users are registered.
Riders may also want to update their phone numbers, which again is handled by RiderAuthorizer.

### AuthorizedRider
Successful login will give you access to instance of AuthorizedRider. This class allows you to confirm that rider has accepted the terms, request a ride, setup payments, access trip history, check if he can request a ride, check if he is alreay in an active ride etc.
After successful login, all operations that a user can do while not in an active ride will be avaliable with AurhorizedRider.

### Ride
Once the AuthorzedRider requests a ride, we return and track an instance of Ride. All operations and updates on the ride will be available via this instance. To request a ride, rider will specify the locations, car types, driver comments. Once the request is received, ride changes state from Requesting to driver assigned and so on till ride completed. 
One can also perform cancelling ride operation or contacting driver operation. Once the ride ends, rider can also give tip to drivers.
    

### Digging deeper
The above concepts actually encapsulates the core service modules of the system which are as below:

#### 1. RideStatusService

Foreground service which listens to ride status changes.
Application will keep `RideStatusService` alive (using `startForeground` and `STICKY` mode) during the ride.
When there is no active ride service is shut down.

#### 2. StateManager

Keeps track of current ride and unrated ride (if any).
Exposes reactive API for publish-subscribe pattern. Model in MVVM.
`StateManager` is bound to Android `Application`'s lifecycle.

#### 3. DataManager

Stores session data and encapsulates networking.
Exposes reactive API for publish-subscribe pattern. Model in MVVM.
`DataManager` is bound to Android `Application`'s lifecycle.

#### 4. Managers

There is a bunch of specialized managers which are:

* `ConfigurationManager` updates configuration based on location
* `LocationManager` provides location updates
* `PrefManager` persists user data
* `AppNotificationManager` manages device notifications and in-popupAppManager messages
* `ConnectionStateManager` listens to network and server reachability