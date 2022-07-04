#General Issues

1. If you direct try to intialize the RWRiderWrapper class before calling the steup then you will get the below exception - 
               "Error - you must call setup before accessing RWRiderWrapper.sharedInstance"
               
Resolution - Please call the setup method before using the shared instance of RWRiderWrapper.

2. If you direct try to intialize the RWRiderAPIWrapper class before calling the setupClient then you will get the below exception - 
                "Error - you must call setup before accessing RWRiderWrapper.sharedInstance"
               
Resolution - Please call the setupClient method before using the shared instance of RWRiderWrapper.
