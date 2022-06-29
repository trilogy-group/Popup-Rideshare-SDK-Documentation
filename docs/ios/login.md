## All methods should call after setup the RWRiderAPIWrapper.
We have configured all the methods which are required for login under login delegate. We can get the instance of login delegate with below syntax - 
```Objc
[RWRiderAPIWrapper loginDelegate]
```
Below are methods which are available under login delegate - 
```objc
-(void)sendOTPInPhone:(NSString *)phoneNumber withCompletion:(RWSendOTPCompletionBlock)handler;
-(void)verifyOTPWithCode:(nonnull NSString *)code phoneNumber:(nonnull NSString *)phoneNumber token:(nonnull NSString *)token withCompletion:(nonnull RWLoginCompletionBlock)handler;
-(void)loginWithUsername:(nonnull NSString *)username password:(nonnull NSString *)password andCompletion:(nonnull RWLoginCompletionBlock)handler;
```
