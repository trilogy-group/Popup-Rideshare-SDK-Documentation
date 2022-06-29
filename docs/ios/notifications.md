###Enable Push Notification

We can enable the push notifications in our sdk. 
We need to provide the delegate as an input to get the call back from our OS regarding the notfication. We have also configured the functionality for a client app to identify wheather the notifiaction is from client app or our sdk.

```swift
RWRiderWrapper.sharedInstance.registerForPushNotification(delegate: self)
```
After register we need to implement two delegate methods to get the notifications - 
```swift
func application(_ application: UIApplication, didRegisterForRemoteNotificationsWithDeviceToken deviceToken: Data) {
    RWRiderWrapper.sharedInstance.application(didRegisterForRemoteNotificationsWithDeviceToken: deviceToken)
}
func userNotificationCenter(_ center: UNUserNotificationCenter, didReceive response: UNNotificationResponse, withCompletionHandler completionHandler: @escaping () -> Void) {
    if RWRiderWrapper.sharedInstance.isPopupRiderNotification(response: response) {
        RWRiderWrapper.sharedInstance.processPopupRiderNotification(response: response)
    }
}
```
Below method can be used to identify wheather the notification is from client app or sdk. If the notification is from sdk then it will return true.
```swift
public func isPopupRiderNotification(response: UNNotificationResponse) -> Bool
```
