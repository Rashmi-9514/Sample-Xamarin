
## Example C# Usage

#### Grab a reference  
```javascript 
private CleverTapAPI cleverTapAPI;
cleverTapAPI = CleverTapAPI.GetDefaultInstance(Android.App.Application.Context);
```

## User Properties

#### Update User Profile(Push Profile )
```javascript 
IDictionary<string, Java.Lang.Object> profileData = new Dictionary<string, Java.Lang.Object>();

            profileData.Add("Name", "user1");    // String
            profileData.Add("Identity", 97839492);      // String or number
            profileData.Add("Email", "user1@gmail.com"); // Email address of the user
            profileData.Add("Phone", "7012801820919");   // Phone (with the country code, starting with +)
            profileData.Add("Gender", "M");             // Can be either M or F
            profileData.Add("DOB", new Date());         // Date of Birth. Set the Date object to the appropriate value first - requires java.util


            cleverTapAPI.PushProfile(profileData);;
```
#### Update User Profile(OnUserLogin Profile )
```javascript 
IDictionary<string, Java.Lang.Object> profile = new Dictionary<string, Java.Lang.Object>();

            profile.Add("Name", "user2");    // String
            profile.Add("Identity", 321323112);      // String or number
            profile.Add("Email", "user2@gmail.com"); // Email address of the user
            profile.Add("Phone", "1212");   // Phone (with the country code, starting with +)
            profile.Add("Gender", "M");               // Can be either M or F
            profile.Add("DOB", new Date());         // Date of Birth. Set the Date object to the appropriate value first - requires java.util

            cleverTapAPI.OnUserLogin(profile);
```	    
#### Record an event  
```javascript 
 cleverTapAPI.PushEvent("Product View Via Xamarin");
```

#### Record Charged event
```javascript 
 IDictionary<string, Java.Lang.Object> chargedDetails = new Dictionary<string, Java.Lang.Object>();
            chargedDetails.Add("Total Amount", 400);

            IDictionary<string, Java.Lang.Object> item1 = new Dictionary<string, Java.Lang.Object>();
            item1.Add("Product Name", "Harry Potter");
            item1.Add("ProductID", "4756");
            item1.Add("Price", 300);

            IDictionary<string, Java.Lang.Object> item2 = new Dictionary<string, Java.Lang.Object>();
            item2.Add("Product Name", "Harry Potter 2");
            item2.Add("ProductID", "4776");
            item2.Add("Price", 100);

            List<IDictionary<string, Java.Lang.Object>> items = new List<IDictionary<string, Java.Lang.Object>>();
            items.Add(item1);
            items.Add(item2);

            cleverTapAPI.PushChargedEvent(chargedDetails, items);
```


## App Inbox

#### Initialize the CleverTap App Inbox Method
```javascript 
cleverTapAPI.CTNotificationInboxListener = (ICTInboxListener)this;
            cleverTapAPI.SetInboxMessageButtonListener((IInboxMessageButtonListener)this);
            cleverTapAPI.InitializeInbox();
```

#### Show the App Inbox
```javascript
IList<string> tabs = new List<string>();
            tabs.Add("Promotions");
            tabs.Add("Offers");
            tabs.Add("Others");//We support upto 2 tabs only. Additional tabs will be ignored

            CTInboxStyleConfig styleConfig = new CTInboxStyleConfig();
            styleConfig.Tabs = tabs;//Do not use this if you don't want to use tabs
            styleConfig.TabBackgroundColor = "#FF0000";//provide Hex code in string ONLY
            styleConfig.SelectedTabIndicatorColor = "#0000FF";
            styleConfig.SelectedTabColor = "#000000";
            styleConfig.UnselectedTabColor = "#FFFFFF";
            styleConfig.BackButtonColor = "#FF0000";
            styleConfig.NavBarTitleColor = "#FF0000";
            styleConfig.NavBarTitle = "MY INBOX";
            styleConfig.NavBarColor = "#FFFFFF";
            styleConfig.InboxBackgroundColor = "#00FF00";

            cleverTapAPI.ShowAppInbox(styleConfig);
 ```

#### Get Total message count
```javascript 
CleverTap.getInboxMessageCount((err, res) => {
				console.log('Total Messages: ', res, err);
				alert(`Total Messages: \n ${res}`);
			});	
```


## Push Notifications

#### Creating Notification Channel
```javascript 
  CleverTapAPI.CreateNotificationChannel(Android.App.Application.Context, "BRTesting", "BRTesting", "BRTesting", 5, true);			
```

#### Creating a group notification channel
```javascript 
CleverTapAPI.CreateNotificationChannelGroup(Android.App.Application.Context, "YourGroupId", "Your Group Name");	
```

## Native Display

#### Get Display Unit for Id
```javascript 
 cleverTapAPI.SetDisplayUnitListener((Com.Clevertap.Android.Sdk.Displayunits.IDisplayUnitListener)this);
```

## Product Config 

#### Set Product Configuration to default
```javascript 
cleverTapAPI.SetCTProductConfigListener((Com.Clevertap.Android.Sdk.Product_config.ICTProductConfigListener)this);
```

#### Fetching product configs
```javascript 
 cleverTapAPI.ProductConfig().Fetch(0);
```

#### Activate the most recently fetched product config
```javascript 
cleverTapAPI.ProductConfig().Activate();
```
## Feature Flag

#### Get Feature Flag
```javascript 
cleverTapAPI.SetCTFeatureFlagsListener((ICTFeatureFlagsListener)this);
```

## Attributions

#### Get CleverTap Attribution Identifier
```javascript 

cleverTapAPI = CleverTapAPI.GetDefaultInstance(Android.App.Application.Context);
```
## Debug Level

#### Set Debug Level
```javascript 
CleverTapAPI.SetDebugLevel(CleverTapAPI.LogLevel.Debug);
```






### For more information,
 - [see included Starter Application](https://github.com/CleverTap/clevertap-react-native/blob/master/Starter/App.js) 
 - [see CleverTap JS interface](https://github.com/CleverTap/clevertap-react-native/blob/master/index.js)
 - [see CleverTap TS interface](https://github.com/CleverTap/clevertap-react-native/blob/master/index.d.ts)
