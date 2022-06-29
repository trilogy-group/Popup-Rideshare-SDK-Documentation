## All methods should call after setup the RWRiderAPIWrapper.
We have configured all the methods which are required for registration under register delegate. We can get the instance of register delegate with below syntax - 
```Objc
[RWRiderAPIWrapper registerDelegate]
```
Below are methods which are available under register delegate - 
```objc
-(void)checkAvailabilityOfEmail:(NSString*)email andPhone:(NSString*)phoneNumber withCompletion:(RWCheckResponseBlock)handler;
-(void)sendOTPInPhone:(NSString *)phoneNumber withCompletion:(RWSendOTPCompletionBlock)handler;
-(void)verifyOTPWithCode:(NSString *)code token:(NSString *)token withCompletion:(RWVerifyOTPCompletionBlock)handler;
-(void)registerWithFirstName:(NSString *)firstName lastName:(NSString*)lastName email:(NSString*)email password:(NSString*)password phone:(NSString*)phone andCompletion:(RWLoginCompletionBlock)handler;
```
