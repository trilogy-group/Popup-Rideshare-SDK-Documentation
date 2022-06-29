##RWRiderWrapper
This is the only class which will responsible to do all the communication with client app. This is a singleton class and client app will use the shared instance to manage the single session. 

This class will take setup config as a required parameter before creating the instance. So we need to provide the configuration before using the instance of this class.

``` swift linenums="1"
    public class func setup(_ config:RWRiderConfig)
```

Structure of RWRiderConfig

```` swift
// clientCode - this will be your sdk key
    public init(clientCode: String) 
// Intializing by setting prefilled registration info in registration screen
    public init(clientCode: String, registerInfo: RWRiderRegisterInfo ) 
// Use this method to show driver registration functionality in sdk. It will not present by default
    public func showDriverRegistration() 
// Use this method to show campaignfunctionality in sdk. It will not present by default
    public func showCampaign() 
// Use this method to show promotion functionality in sdk. It will not present by default
    public func showPromocode() 
// Use this method to change the registration method. It is set to .OTP by default
    public func setRegistrationMethod(method: RegistrationMethod) 
````
Structure of RWRiderRegisterInfo

````swift
public init(firstName: String?, lastName: String?, email: String?)
````

Here Registration method is enum which has three types. below is the structure - 

OTP - It will show the mobile number authentication in registration. It will not take any password input during the registration.

Passsword - It will show the password authentication in registration. It will not take any mobile number input during the registration.

PasswordWithOTP - It will show the password along with mobile number authentication in registration. It will not take both mobile number and password input during the registration.

``` swift
{ #example .OTP, .Passsword, .PasswordWithOTP }
public enum RegistrationMethod: Int{
    case OTP = 1
    case Passsword
    case PasswordWithOTP
}
```
