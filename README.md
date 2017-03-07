# React Native Twilio Chat
<<<<<<< HEAD
[![npm version](https://badge.fury.io/js/react-native-twilio-ip-messaging.svg)](https://badge.fury.io/js/react-native-twilio-ip-messaging)

>React Native wrapper for the Twilio IP Messaging SDKs

**Updated to new SDKs for Twilio Chat -- this has breaking changes if you were on the prior IPM versions**

####[Changelog](CHANGELOG.md)

## Installation
```npm install --save react-native-twilio-ip-messaging```
=======

>React Native wrapper for the Twilio Programmable Chat iOS and Android SDKs

*Note - this project is currently in development for a beta release. If you are looking for the legacy package for the Twilio IP Messaging SDKs, [see the original repository here](https://github.com/ccm-innovation/react-native-twilio-ip-messaging).*

## Installation
```
npm install --save react-native-twilio-chat
```
>>>>>>> master

### iOS
Install the Twilio Programable Chat SDK and this package via CocoaPods.

<<<<<<< HEAD
```
pod 'React', :subspecs => ['Core', 'RCTActionSheet', 'RCTGeolocation', 'RCTImage', 'RCTLinkingIOS', 'RCTNetwork', 'RCTText', 'RCTSettings', 'RCTAnimation', 'RCTVibration', 'RCTWebSocket'], :path => '../node_modules/react-native'
pod 'RCTTwilioChat', :path => '../node_modules/react-native-twilio-ip-messaging/ios'
=======
```ruby
pod 'React', :subspecs => ['Core', /* any other subspecs you require */], :path => '../node_modules/react-native'
pod 'RCTTwilioChat', :path => '../node_modules/react-native-twilio-chat/ios'
>>>>>>> master
  
source 'https://github.com/twilio/cocoapod-specs'
pod 'TwilioChatClient', '~> 0.16.0'
pod 'TwilioAccessManager', '~> 0.1.1'
```
**Note: the underlying Twilio SDKs require a minimum deployment target of `8.1`**. If your project's target is less than this you will get a CocoaPods install error (`Unable to satisfy the following requirements...`).

<<<<<<< HEAD
Make sure that you add the `$(inherited)` value to `Other Linker Flags` and `Framework Search Paths` for your target's Build Settings. This is also assuming you have already loaded React via CocoaPods as well.
=======
Make sure that you add the `$(inherited)` value to `Other Linker Flags` and `Framework Search Paths` for your target's Build Settings.
>>>>>>> master
            
### Android
In `android/settings.gradle`:

<<<<<<< HEAD
```
include ':RCTTwilioChat', ':app'
project(':RCTTwilioChat').projectDir = new File(rootProject.projectDir, '../node_modules/react-native-twilio-ip-messaging/android')
```

In `android/app/build.gradle`:
```
=======
```java
include ':RCTTwilioChat', ':app'
project(':RCTTwilioChat').projectDir = new File(rootProject.projectDir, '../node_modules/react-native-twilio-chat/android')
```

In `android/app/build.gradle`:
```java
>>>>>>> master
...
dependencies {
    ...
    compile project(':RCTTwilioChat')
}

```

Register the module in `MainApplication.java`:
```Java
// import package
import com.bradbumbalough.RCTTwilioChat.RCTTwilioChatPackage;

...

// register package in getPackages()
@Override
protected List<ReactPackage> getPackages() {
    return Arrays.<ReactPackage>asList(
        new MainReactPackage(),
        new RCTTwilioChatPackage(),
        ... other packages
    );
}
```

**Note:** You might have to enable multidex in your `build.gradle` file and increase the heap size if you're getting errors while buliding. The minSdkVersion must also be at least 19, per the Twilio SDKs. 
<<<<<<< HEAD
```
=======
```java
>>>>>>> master
android {
    ....
    dexOptions {
        javaMaxHeapSize "2048M"
    }
    
    defaultConfig {
        ...
        minSdkVersion 19
        multiDexEnabled true
    }
```

## Usage
<<<<<<< HEAD
```JavaScript
=======
```javascript
>>>>>>> master
/* Initialization */

import {
    AccessManager,
    Client,
    Constants
<<<<<<< HEAD
} from 'react-native-twilio-ip-messaging';
=======
} from 'react-native-twilio-chat';
>>>>>>> master

// create the access manager
const accessManager = new AccessManager(token);

// specify any handlers for events
accessManager.onTokenWillExpire = () => {
    getNewTokenFromServer()
    .then(accessManager.updateToken);
}

// create the client
const client = new Client(token);

// specify any global events
<<<<<<< HEAD
client.onError = ({error, userInfo}) => console.log(error)
=======
client.onError = ({error, userInfo}) => console.log(error);
>>>>>>> master

// initialize the client
client.initialize();

// wait for sync to finish
client.onClientSynchronized = () => {
    client.getUserChannels()
    .then((channelPaginator) => console.log(channelPaginator.items));
}

/* Individual Channel */

// an instance of Channel is passed down in the app via props
let channel = this.props.channel

// specify channel specific events
<<<<<<< HEAD
channel.onMessageAdded = (message) => console.log(message.author + ": " + message.body)
channel.onTypingStarted = (member) => console.log(member.identity + " started typing...")
channel.onTypingEnded = (member) => console.log(member.identity + " stopped typing...")
channel.onMemberAdded = (member) => console.log(member.identity + " joined " + channel.friendlyName)

// sending a message
<TextInput
    onChangeText={(body) => {
        this.setState({body})
        channel.typing()
    }}
    onSubmitEditing={() => channel.sendMessage(this.state.body)}
/>
````

####[Documentation](docs)
=======
channel.onMessageAdded = (message) => console.log(message.author + ": " + message.body);
channel.onTypingStarted = (member) => console.log(member.identity + " started typing...");
channel.onTypingEnded = (member) => console.log(member.identity + " stopped typing...");
channel.onMemberAdded = (member) => console.log(member.identity + " joined " + channel.friendlyName);

// sending a message
<TextInput 
  onChangeText={(body) => {
    this.setState({body});
    channel.typing();
  }}
  onSubmitEditing={() => { channel.sendMessage(this.state.body)} }
/>
````

## [Documentation](docs)

## Contributers 🍻
- [plonkus](https://github.com/plonkus)
- [jhabdas](https://github.com/jhabdas)
- [thathirsch](https://github.com/thathirsch)
- [Baisang](https://github.com/Baisang)
- [jck2](https://github.com/jck2)
- [johndrkurtcom](https://github.com/johndrkurtcom)
- [bradbumbalough](https://github.com/bradbumbalough)

## TODO 🗒
 * [ ] Copy code from `programable-chat` branch on old package
 * [ ] Update docs (wiki?)
 * [ ] Migration guide
 * [ ] Publish to npm
 * [ ] 1.0 release
 * [ ] Testing

## License
This project is licensed under the [MIT License](LICENSE).
>>>>>>> master
