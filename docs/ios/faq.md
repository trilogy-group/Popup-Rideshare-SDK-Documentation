#General Issues

1. If you direct try to initialize the RWRiderWrapper class before calling the steup then you will get the below exception - 

    "Error - you must call setup before accessing RWRiderWrapper.sharedInstance"
    
    Resolution - Please call the setup method before using the shared instance of RWRiderWrapper.

2. If you direct try to initialize the RWRiderAPIWrapper class before calling the setupClient then you will get the below exception - 

    "Error - you must call setup before accessing RWRiderWrapper.sharedInstance"
    
    Resolution - Please call the setupClient method before using the shared instance of RWRiderWrapper.

## Which ios versions are supported ?
iOS 13 and above

## Which language used to develop high level sdk?
Swift

## Which language used to develop low level sdk?
Objective C

## Which language does client app needs to integrate high level sdk?
Either Swift or Objective C

## ## Which language does client app needs to integrate high level sdk?
Either Swift or Objective C

## Why is payment necessary before booking the ride ?
Riders may want to tip the drivers for which they will be charged the tip amount and it is fully given to drivers. Also riders may create a mess in the car for which we need cover damage fees by charging the card.

## Do you store credit card information ?
No we do not store credit card information. We use stripe as payment partner which ensures secure payment processing.

## During development, how do I book fake rides to test ?
Please reach out to support team for this.

## Are phone numbers getting shared with drivers ?
No we use twilio to mask the phone numbers of riders.

## Can we dynamically increase availability of cars based on demand ?
Kindly reach out to support team so that we can understand your requirements.

## what are airport cars ?
Due to legal restrictions, cars which are wrapped with marketing messages are not allowed to enter airport pickups and drops. Thus we need to have a separate pool of non marketing cars to fulfill airport rides.

## Does the sdk support non English language ?
No, currently we only support English language.


