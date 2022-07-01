
When using the sdk in this mode you need to create a config object which will be used in initialization, 
implement necessary method to ensure notifications are processed 
and then configure some UI element in your app which will launch the Popup Sdk UI.

Following concepts are involved in using the sdk in this mode.

## Architecture
We have the standard client server architecture where the sdk acts as client and integrates with Popup Server for ride hailing.
Apart from Popup Backend Server, the sdk also interacts with Goggle Maps server to show the maps. It also interacts with Stripe server to process the payments. Lastly Google Firebase sends out notifications to your app and Popup's notification will be passed to the sdk.

## Google Play Resources
Google Maps platform is accessed via sdk key in the app which will be restricted for use only from within your app.
This requires us to register your app information with Google maps platform.
You must already have a registered app in the play store account. You will need to share the application id and sha-1 fingerprint of the apps public certificate. 

## Popup Config
During the onboarding process, our team will share an sdk key with you. You use that sdk key to create a Popup Config object as shown in getting started. You can also append your own logger if you wish. If you use Firebase Crashlytics, configure the same in config and the sdk will automatically upload extra log and data with crashes if any.

## Popup Notifications
For Popup Server to send notifications to your apps, it needs to authenticate itself with Google. This requires you to share api key with us furing onboarding which is available in your firebase project settings under Cloud Messaging.
Popup sends notification to let riders know if Driver has been allocated, driver has arrived etc. This is important because riders often lock their phone or switch apps while waiting and rely on notifications to let them know. 
Alternately we can send sms instead of notifications but they are not reliable and are often delivered much late than needed.

You will need to implement a notification receiver, if you dont already have one, to receive notifications from google. How to do this is shown in the getting started. The sdk supplies method to check if the received notification is meant for popup. If yes, you can launch the Popup to process the notification

## Lauching the SDK
After initalizing the sdk, you can simply configure call the launch function on some UI element of your app.
This will essentially launch a new activity and take the user to Popup's home screen. If user is not already registered, he will need to register first and accept Popup Terms and Conditions.

If you want to know about the internal components of SDK, look into Build and integrate mode.

## Payments
After launching the sdk, for the first time user, you will see the sdk requests to add payment methods before allowing to book ride.
We dont save any credit card information and instead rely on stripe as payment partner to securely process payments.
While the rides are normally free, we still need payment information in case rider wants to give additional tip to drivers or if they make a mess in car and need to cover damages.

Next refer to Getting started or go over to Build and Integrate if interested to know internal details about sdk.
