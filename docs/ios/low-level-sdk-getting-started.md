# Integrate Low level sdk

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

pod 'RWRiderSDKAPI'

Github repo - 

####How to use in Swift

```swift
import RWRiderSDKAPI
```
####How to use in Objective C
```objc
import <RWRiderSDKAPI/RWRiderSDKAPI.h>
```
