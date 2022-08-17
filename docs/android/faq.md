## Which Android versions are supported ?
Android API level 21 and above are supported.

## Why is payment necessary before booking the ride ?
Riders may want to tip the drivers for which they will be charged the tip amount and it is fully given to drivers. Also riders may create a mess in the car for which we need cover damage fees by charging the card.

## Do you store credit card information ?
No we do not store credit card information. We use stripe as payment partner which ensures secure payment processing.

## During development, how do I book fake rides to test ?
You can use test environment which allows adding a fake credit card in payments.
To use test environment, just change your gradle dependency to below

```java
implementation "com.messageone:popup-android-test-env:$latest_version"
```
You can use below as fake credit card.
```
card number : 4242 4242 4242 4242
Cvv : any three digit number
exp date : any future date
```
You will also need to be a fake driver to accept ride requests and fulfill them with fake gps.
To be a fake driver, contact support to supply Driver app for the test environment.

## Are phone numbers getting shared with drivers ?
No we use twilio to mask the phone numbers of riders.

## Why is contacting driver/rider not working in test environment ?
Calling/sms feature are not supported in test environment to prevent unregulated telecom charges.

## Can we dynamically increase availability of cars based on demand ?
Kindly reach out to support team so that we can understand your requirements.

## what are airport cars ?
Due to legal restrictions, cars which are wrapped with marketing messages are not allowed to enter airport pickups and drops. Thus we need to have a separate pool of non marketing cars to fulfill airport rides.

## How can i customize UI with color palette and other minor modifications ?
This feature is a work in progress and will be available in future. Let us know if this is important for you so that we can prioritize accordingly.

## Does the sdk support non English language ?
No, currently we only support English language.