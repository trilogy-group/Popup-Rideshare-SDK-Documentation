## All methods should call after setup the RWRiderAPIWrapper.
We have configured all the methods which are required for forgot password under forgotPassword delegate. We can get the instance of forgotPassword delegate with below syntax - 
```Objc
[RWRiderAPIWrapper forgotPasswordDelegate]
```
Below are methods which are available under forgotPassword delegate - 
```objc
-(void)recoverPasswordFromEmail:(NSString *)email withCompletion:(RWRecoverPasswordCompletionBlock)handler;
```
