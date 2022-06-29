##RWRiderAPIWrapper

This is the entry point class for low level sdk which is used to set the configuration for low level sdk. This will take only sdk key(clientCode) as an input paramter. This will also create the single instance to manage the session through the life cycle of app.
Client needs to call the setup method before using the shared instance of the class. Below is declaration of setup method - 

```ObjC
+(void)setupClient:(NSString*)clientCode 
```
