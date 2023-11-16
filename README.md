## reactNativeCheetSheet
In this folder i  will share full  guideline for neactNative app development process step by step
![ReactNative](https://reactnative.dev/img/tiny_logo.png)
All Design URL list:
## Important LINK for Developing
 [CSS Flex Box](https://www.youtube.com/watch?v=phWxA89Dy94) \
 [Random Images LINK](https://picsum.photos/)

### Starting command 
npx create-expo-app jobSearch

### start android emulator using  expo-go following this command 
=> npm install -g expo-cli \
=> expo-cli start --tunnel

## Components 
### View 

The <View> component in React Native acts as a container for organizing and styling other UI components. It creates a structured layout, holds child components,thats means a div. 
Example:

```
import React from 'react';
import { View, Text, StyleSheet } from 'react-native';

const App = () => {
  return (
    <View style={styles.container}>
      <Text>Hello, React Native!</Text>
    </View>
  );
};

const styles = StyleSheet.create({
  container: {
    flex: 1,
    justifyContent: 'center',
    alignItems: 'center',
    backgroundColor: '#f0f0f0',
  },
});

export default App;
```
### Text
Component for displaying text , it supports nesting, styling and touch handling, Depending on the  target platform , React Native will translate this component to either a UI TextView(IOS), a textView  or a 'p' (web)
```
import React from 'react';
import { View, Text, StyleSheet } from 'react-native';

const MyTextComponent = () => {
  return (
    <View style={styles.container}>
      <Text>Hello, React Native!</Text>
    </View>
  );
};

const styles = StyleSheet.create({
  container: {
    flex: 1,
    justifyContent: 'center',
    alignItems: 'center',
  },
});

export default MyTextComponent;
```

### Images
Image component enables us to display various types of images, including  Static, Networking and images from the local disk, such as the camera roll.


