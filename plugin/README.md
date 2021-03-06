# Zendesk Plugin for the NativeScript framework

## Setup
- Create your Mobile SDK account in zendesk
- https://domain.zendesk.com/agent/admin/mobile_sdk
- Note your appid, url, and clientid for later
- Make sure to activate your help center (if you want it) in your MobileSDK->Customization screen

Add the plugin
```js
var zendeskModule = require("nativescript-zendesk");
var zendesk = null; // Place to store the activated object

//Somewhere on load
zendesk = zendeskModule.init(<appid>,<url>,<clientid>,<enablelogging (optional)>);
```

Open the Help Center
```js
zendesk.openHelpCenter();
```

Open the Contact Screen
```js
zendesk.openContact();
```

## Options
Set locale
```
zendesk.setLocale("fr_CA");
```

Set identify a user
```js
    zendesk.identifyUser("users id", "some user name", "fake@thisuser.com"); //Optional, defaults to anon if not set
        
    zendesk.openContact();
```

### iOS Theme
[Docs](https://developer.zendesk.com/embeddables/docs/ios/customization)
```

//Create the theme
//All of these properties are optional...and it's all grey, so dont use colors verbatim :)
var myTheme = {
	ZDKSupportView: {
		viewBackgroundColor: "#E0E0E0",
		tableBackgroundColor: "#E0E0E0",
		separatorColor: "#E0E0E0",
	
		//0 = light, 1=dark
		searchBarStyle: 0,
		
		noResults: {
			foundLabelColor: "#E0E0E0",
			foundLabelBackground: "#E0E0E0",
			contactButtonBackground: "#E0E0E0",
			contactButtonTitleColorNormal: "#E0E0E0",
			contactButtonTitleColorHighlighted: "#E0E0E0",
			contactButtonTitleColorDisabled: "#E0E0E0",
			contactButtonBorderColor: "#E0E0E0",	
			foundLabelFont: UIFont.fontWithNameSize("Lato", 16),
			contactButtonBorderWidth: 1.0,
			contactButtonCornerRadius: 4.0
		} 
	},
	ZDKSupportTableViewCell: {
		viewBackgroundColor: "#E0E0E0",
		titleLabelBackground: "#E0E0E0",
		titleLabelColor: "#E0E0E0",
		titleLabelFont: UIFont.fontWithNameSize("Lato", 16)
	},
	ZDKSupportArticleTableViewCell: {
		viewBackgroundColor: "#E0E0E0",
		parentsLabelColor: "#E0E0E0",
		parnetsLabelBackground: "#E0E0E0",
		titleLabelColor: "#E0E0E0",
		labelBackground: "#E0E0E0",
		titleLabelFont: UIFont.fontWithNameSize("Lato", 16),
		articleParentsLabelFont: UIFont.fontWithNameSize("Lato", 16)
	},
	ZDKSupportAttachmentCell: {
		backgroundColor: "#E0E0E0",
		titleLabelBackground: "#E0E0E0",
		titleLabelColor: "#E0E0E0",
		fileSizeLabelBackground: "#E0E0E0",
		fileSizeLabelColor: "#E0E0E0",
		titleLabelFont: UIFont.fontWithNameSize("Lato", 16),
		fileSizeLabelFont: UIFont.fontWithNameSize("Lato", 16)
	}
};
	
//Load the theme
zendesk.setTheme(myTheme);

```

### Android Theme
None of the iOS methods work for android, styling is done in the Manifest (see the one in the plugin directory)

Example:
```
<activity android:name="com.zendesk.sdk.support.SupportActivity" android:theme="@style/Theme.AppCompat.Light"/>
```

NativeScripts default theme is 

[Docs](https://developer.zendesk.com/embeddables/docs/android/customization)
