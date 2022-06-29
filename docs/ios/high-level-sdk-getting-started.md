# Integrate high level sdk
##Integration with pod
We have configured the XCframework with pod. You can install the sdk by adding the pod dependency to your project. 
If you have not configures the pod dependency then please follow the below steps to add the pod depenency - 

1. Open the terminal
2. Command on the terminal: sudo gem install cocoapods
3. Set your project path in the terminal.
4. Command: pod init
5. Go to the pod file of your project and add the pod which you want to install
6. Added in the pod file: pod 'RWRiderSDK'
7. Command: Pod install
8. Close the Xcode project
9. open your project from the terminal
10. Command: open <projectName>.xcworkspace


If You have already added the pod depencency to you project then please skip the above 5 steps and follow after 5th step.

Please find the below pod details - 

pod 'RWRiderSDK'

Github repo - 

####How to use in Swift
```swift
import RWRider
```

####How to use in Objective C
```objc
import <RWRider/RWRider.h>
```

## Launch the sdk

We just need to call the single method to launch the sdk. Please make sure this should called after steup.
``` swift
public func root(delegate: RWRiderSDKDelegate?) -> UINavigationController
```
Please find the below snippet code to launch the sdk from window scene //eg.
```swift
let window = UIWindow(windowScene: windowScene)
let wrapper = RWRiderWrapper.sharedInstance
window.rootViewController = wrapper.root(delegate: self)
self.window = window
window.makeKeyAndVisible()
```
Please find the below code to launch the sdk from any other controller.
``` swift
let wrapper = RWRiderWrapper.sharedInstance
self.present(wrapper.root(delegate: self), animated: true, completion: nil)
```
We have taken the delegate as an input. this delegate will provide one below method ot get the notifiaction from sdk if close button tapped from sdk in splash screen of sdk - 
```swift
func close()
```

Exapmle code for intializing and launching the sdk 

```swift
let config = RWRiderConfig(clientCode: <sdkKey>)
config.showCampaign()
config.showPromocode()
config.showDriverRegistration()
config.setRegistrationMethod(method: .PasswordWithOTP)
RWRiderWrapper.setup(config)
let wrapper = RWRiderWrapper.sharedInstance
wrapper.registerForPushNotification(delegate: self)
self.present(wrapper.root(delegate: self), animated: true, completion: nil)
```
