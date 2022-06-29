#RWRiderClient

## Client will get the instance of this class after login.

Client will be able to play all ride hail operation with these instance.
Below are the instance properties are available for this instance
```objc
@property(weak, nonatomic) id <RWRiderClientDelegate> delegate;
@property (weak, nonatomic) RARiderDataModel *rider;
@property (nonatomic, readonly, getter=isDriverComing) BOOL driverComing;
@property (nonatomic, readonly, getter=isDriverArrived) BOOL driverArrived;
@property (nonatomic, readonly, getter=isOnTrip) BOOL onTrip;
@property (nonatomic, readonly, getter=isRiding) BOOL riding;
@property (nonatomic, readonly, getter=isStartLocationSelected) BOOL startLocationSelected;
@property (nonatomic, readonly, getter=isDestinationLocationSelected) BOOL destinationLocationSelected;
```
Below are the instance methods are available for this instance
```objc
-(instancetype)initWithRider:(RARiderDataModel * _Nullable)dataModel;
-(BOOL)hasUnpaidBalance;
-(BOOL)isRiding;
-(void)startPollingForActiveDrivers;
-(void)stopPollingForActiveDrivers;
-(void)getNearestDriversWithStartLocation:(CLLocationCoordinate2D)startLocation andSelectedCategory:(RACarCategoryDataModel*)category withCompletion:(RAActiveDriversAPICompletionlock)handler;
-(void)reloadCurrentRiderWithCompletion:(void (^)(RARiderDataModel *rider, NSError *error))completion;
-(void)requestRide:(RARideRequest *)rideRequest withCompletion:(RARideStatusCodeCompletionBlock)handler;
-(void)postRidesQueue:(NSString * _Nonnull)token withCompletion:(RARideCompletionBlock)completion;
-(void)cancelRideById:(NSString*)rideID withCompletion:(APIErrorResponseBlock)handler;
-(void)getRide:(NSString *)rideID andCompletion:(RARideCompletionBlock)handler;
-(void)getRide:(NSString*)rideID withRiderLocation:(nullable CLLocation *)riderLocation andCompletion:(RARideCompletionBlock)handler;
-(void)restoreRide:(RARideDataModel *)ride;
-(void)updateDestination:(RARideLocationDataModel*)destination forRide:(NSString*)rideID completion:(APIErrorResponseBlock)handler;
-(void)updateComment:(NSString*)comment forRide:(NSString*)rideID completion:(APIErrorResponseBlock)handler;
```
Below are the instance methods are available for this instance to perform upgrade request operation
```objc
-(void)declineUpgradingCurrentRideWithCompletion:(APIErrorResponseBlock)handler;
-(void)confirmUpgradingCurrentRideWithCompletion:(APIErrorResponseBlock)handler;
```
Below are the instance methods are available for this instance to perform cancelation feedback operation
```objc
-(void)getReasonsWithCompletion:(void(^)(NSArray<CFReasonDataModel *> * _Nullable reasons, NSError * _Nullable error))completion;
-(void)postReason:(NSString *)reasonCode forRide:(NSNumber *)rideID withComment:(NSString *)comment andCompletion:(void (^)(NSError * _Nullable))completion;
```
Below are the instance methods are available for this instance to perform costs related operation
```objc
-(void)getSpecialFeesAtCoordinate:(CLLocationCoordinate2D)coordinate
                           cityID:(NSNumber *)cityID
                   forCarCategory:(NSString *)carCategory
                   withCompletion:(void(^)(NSArray<RAFee *> * _Nullable specialFees, NSError * _Nullable error))completion;

-(void)getRideEstimateFromStartLocation:(CLLocationCoordinate2D)startLocation
                          toEndLocation:(CLLocationCoordinate2D)endLocation
                             inCategory:(RACarCategoryDataModel*)category
                         withCompletion:(void (^)(RAEstimate * _Nullable estimate, NSError * _Nullable))completion;
```
Below are the instance methods are available for this instance to perform complete ride related operation
```objc
/**
 @param paymentProvider if specified as CREDIT_CARD, server will not wait for paymentDelays and immediately charge the primary credit card
 */
-(void)rateRide:(NSString *)rideID
     withRating:(NSString *)rating
            tip:(NSString *)tip
     andComment:(NSString *)comment
paymentProvider:(NSString *)paymentProvider
 withCompletion:(RARideCompletionBlock)completion;
```
Below are the instance methods are available for this instance to get Rider information
```objc
-(void)getCurrentRiderWithCompletion:(RARiderCompletionBlock _Nonnull)handler;
-(void)updateRider:(RARiderDataModel* _Nonnull)rider completion:(NetworkCompletionBlock _Nonnull)handler;
```
Below are the instance methods are available for this instance to get real time tracking
```objc
-(void)getMapForRide:(NSString *)rideID withCompletion:(void (^)(NSURL *mapURL, NSError *error))completion;
```
Below are the instance methods are available for this instance to do charity
```objc
-(void)updateCurrentRiderCharity:(RACharityDataModel* _Nullable)charity withCompletion:(NetworkCompletionBlock _Nonnull)handler;
```
Below are the instance methods are available for this instance to do cards related operation
```objc
-(void)addCardForRider:(NSString* _Nonnull)riderId token:(NSString* _Nonnull)cardToken withCompletion:(CardCreatedBlock _Nonnull)handler;
-(void)setPrimaryCard:(RACardDataModel* _Nonnull)card toRider:(NSString* _Nonnull)riderId withCompletion:(PrimaryCardBlock _Nonnull)handler;
-(void)deleteCard:(RACardDataModel* _Nonnull)card fromRider:(NSString* _Nonnull)riderId withCompletion:(DeleteCardBlock _Nonnull)handler;
-(void)updateCard:(RACardDataModel *_Nonnull)card forRideWithId:(NSString * _Nonnull)riderId expMonth:(NSString *_Nullable)month expYear:(NSString *_Nullable)year withCompletion:(APIErrorResponseBlock _Nonnull)handler;
```
Below are the instance methods are available for this instance to do balance related operation
```objc
-(void)payUnpaidBalanceForRiderWithId:(NSString* _Nonnull)riderId rideId:(NSString* _Nonnull)rideId applePayToken:(NSString* _Nullable)applePayToken completion:(APIErrorResponseBlock _Nonnull)handler;
-(void)redemptionsRemainderForRiderWithId:(NSString* _Nonnull)riderId completion:(APIResponseBlock _Nonnull)completion;
-(void)redemptionsForRiderWithId:(NSString* _Nonnull)riderId completion:(RedemptionsBlock _Nonnull)completion;
```
Below are the instance methods are available for this instance to get trip history
```objc
-(void)getTripHistoryWithRiderId:(NSString *)riderId limit:(NSNumber *)pageSize offset:(NSNumber *)page completion:(TripHistoryCompletion)handler;
```
Below are the instance methods are available for this instance to do user profile operation
```objc
-(void)updateUserEmail:(NSString *)email firstname:(NSString *)firstname lastname:(NSString *)lastname phoneNumber:(NSString *)phoneNumber withCompletion:(RAUpdateUserCompletionBlock)handler;
-(void)checkAvailabilityOfPhone:(NSString*)newPhone;
-(void)updateUserPhoto:(UIImage*)photo withCompletion:(RAUpdateUserCompletionBlock)handler;
-(void)registerPushNotificationsToken:(NSString*)token withCompletion:(void(^)(NSError *error))completion;
```
Below are the instance methods are available for this instance to do support related eoperation
```objc
-(void)getSupportTopicListWithCompletion:(SupportTopicBlock _Nonnull )handler;
-(void)getTopicsWithParentId:(NSNumber*_Nonnull)parentTopicId withCompletion:(SupportTopicBlock _Nonnull )handler;
-(void)getFormForTopic:(SupportTopic *_Nonnull)topic
         withCompletion:(void(^_Nonnull)(LIOptionDataModel *_Nullable, NSError *_Nullable))completion;
-(void)postSupportMessage:(NSString*_Nonnull)comment supportTopic:(SupportTopic*_Nonnull)supportTopic rideId:(NSNumber*_Nonnull)rideId withCompletion:(SupportTopicPostMessageBlock _Nonnull )handler;
-(void)postSupportMessage:(NSString*_Nonnull)message rideID:(NSString *_Nullable)rideID cityID:(NSNumber *_Nullable)cityID withCompletion:(void(^_Nonnull)(NSError * _Nullable error))completion;
-(void)postLostAndFoundLostParameters:(NSDictionary *_Nonnull)params
                        withCompletion:(LostAndFoundBlock _Nonnull )completion;
-(void)postLostAndFoundContactParameters:(NSDictionary *_Nonnull)params
                           withCompletion:(LostAndFoundBlock _Nonnull)completion;
-(void)postLostAndFoundFoundParameters:(NSDictionary *_Nonnull)params
                              andImages:(NSDictionary<NSString *, NSData *> *_Nullable)images
                         withCompletion:(LostAndFoundBlock _Nonnull)completion;
```
Payment Method
```objc
typedef NS_ENUM(NSUInteger, PaymentMethod) {
    PaymentMethodUnspecified = 0,
    PaymentMethodPrimaryCreditCard = 1,
    PaymentMethodBevoBucks = 2,
    PaymentMethodApplePay = 3
};
-(NSString *)paymentMethodRequestParameter {
    switch (self.paymentMethod) {
        case PaymentMethodUnspecified:
        case PaymentMethodApplePay:
            return nil;
        case PaymentMethodBevoBucks:
            return @"BEVO_BUCKS";
        case PaymentMethodPrimaryCreditCard:
            return @"CREDIT_CARD";
    }
}
```

### RWRiderClientDelegate

Client needs to bind with this delegate to observer the ride operation. Below are the events available in this delegate - 
```objc
typedef NS_ENUM(NSInteger,RARideStatus){
    RARideStatusUnknown = 0,    // This one doesn't come from server, it is needed for any new status added on server but not implemented here.
    RARideStatusNone,           // This one doesn't come from server, it is only used to perform UI changes.
    RARideStatusPrepared,       // This one doesn't come from server, it is only used to distinguish it from RARideStatusRequested externally.
    RARideStatusRequesting,     // This one doesn't come from server, it is only used to perform UI changes externally.
    RARideStatusRequested,
    RARideStatusNoAvailableDriver,
    RARideStatusRiderCancelled,
    RARideStatusDriverCancelled,
    RARideStatusAdminCancelled,
    RARideStatusDriverAssigned,
    RARideStatusDriverReached,
    RARideStatusActive,
    RARideStatusCompleted
};
@protocol RWRiderClientDelegate <NSObject>
-(void)changeRideStatus:(RARideStatus)status;
-(void)updateEstimationCompletion:(NSDate*_Nullable)date;
-(void)updatePrecedingMarker:(CLLocationCoordinate2D)coordinate;
-(void)activeDriverLocationChange:(CLLocation*_Nullable)newLocation;
-(void)updateCarTitle:(NSString*_Nullable)title;
-(void)rideUpgradeRequest:(RARideUpgradeRequestDataModel*_Nullable)requestData;
-(void)pollingError:(NSError*_Nullable)error;
-(void)destinationLocationChange:(CLLocation*_Nullable)newLocation;
@end

```
