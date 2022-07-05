## Sdk features

### What does sdk do ?
  The sdk will allow, within your app, performing various operations on popup service. The operations include:
  
  - registration of account with popup
  - term acceptance by riders
  - requesting a ride
  - receive ride notifications
  - contacting drivers
  - configuring payments

It will also allow other features like trip-history, requesting support, updating profile etc.

### What does sdk not do ?
Following operations are configured during onboarding and are out of scope for the sdk:

- Selecting Car models and Car Types for the fleet
- Selecting Drivers for the fleet
- Marketing related custom configurations like logo, message etc
- GeoFencing requirements to operate within a limited area
- Discounts to be given in a ride
- Report generation

The sdk will automatically adapt to above configurations set during onboarding.

## Using iOS SDK
To make use of Popup RideShare sdk within your app, you start with defining latest sdk library as your dependency in pod file and then run the pod install.

Next, you will need an sdk key from the support team which you will need to create a configuraion object and pass it to setup the sdk.

### SDK Modes
The sdk can be used in two differnt mode.

1. Plug and play 
    - pre-built UI and fully integrated
    - just initialize with configuration object and launch
2. Build and Integrate
    - basic sdk to talk to the server
    - you build your own UI and integration with the server
    - This is required only for customers who must give custom UI and rideFlow

Lets review the concepts in the next section before diving deeper into using the any flavour of the sdk.




