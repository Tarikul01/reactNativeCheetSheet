## reactNativeCheetSheet
In this folder i  will share full  guideline for neactNative app development process step by step
![ReactNative](https://reactnative.dev/img/tiny_logo.png)
All Design URL list:
## Important LINK for Developing
 [CSS Flex Box](https://www.youtube.com/watch?v=phWxA89Dy94) \
 [GET Random Images LINK](https://picsum.photos/)

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
const App = () => {
  return (
    <View style={{
    flex: 1,
    justifyContent: 'center',
    alignItems: 'center',
    backgroundColor: '#f0f0f0',
  }}>
      <Text>Hello, React Native!</Text>
    </View>
  );
};
```
### Text
Component for displaying text , it supports nesting, styling and touch handling, Depending on the  target platform , React Native will translate this component to either a UI TextView(IOS), a textView  or a 'p' (web)
```
const MyTextComponent = () => {
  return (
    <View style={styles.container}>
      <Text>Hello, React Native!</Text>
    </View>
  );
};

```

### Images and Images Background
Image component enables us to display various types of images, including  Static, Networking and images from the local disk, such as the camera roll.
```
const App = () => {
  return (
    <View style={{}>
      {/* Local Image */}
      <Image source={require('./local-image.jpg')} style={{}} />

      {/* Network Image */}
      <Image
        source={{ uri: 'https://example.com/network-image.jpg' }}
        style={{}}
      />
    </View>
  );
};

const App = () => {
  return (
    <ImageBackground
      source={require('./background-image.jpg')}
      style={styles.background}
    >
      <View style={styles.container}>
        <Text style={styles.text}>Hello, ImageBackground!</Text>
      </View>
    </ImageBackground>
  );
};
```

## ScrollView  
ScrollView component  wraps the platform-specific scrolling functionality
ScrollView required a bounded height to function  properly
```
const App = () => {
  return (
    <ScrollView contentContainerStyle={styles.scrollViewContainer}>
      <View style={styles.container}>
        <Text style={styles.text}>Item 1</Text>
        <Text style={styles.text}>Item 2</Text>
        <Text style={styles.text}>Item 3</Text>
        <Text style={styles.text}>Item 4</Text>
        {/* Add more items as needed */}
      </View>
    </ScrollView>
  );
};
const styles = StyleSheet.create({
  scrollViewContainer: {
    flexGrow: 1,
    justifyContent: 'center',
  },
  container: {
    flex: 1,
    justifyContent: 'center',
    alignItems: 'center',
  },
  text: {
    fontSize: 20,
    margin: 10,
  },
});
```
## Button press component
```
const App = () => {
  const handlePress = () => {
    Alert.alert('Button Pressed', 'Hello, React Native!');
  };

  return (
    <View style={styles.container}>
      <Button title="Press Me" onPress={handlePress} />
    </View>
  );
};
```
1. > ### Button pressable
   > Prssable is a wrapper component that detects various stages of press interactions on it's defined children
    ```
   const App = () => {
  const handlePress = () => {
    console.log('Pressable Pressed!');
  };

  return (
    <View style={styles.container}>
      <Pressable onPress={handlePress} style={({ pressed }) => [styles.button, pressed && styles.pressedButton]}>
        <Text style={styles.text}>Press Me</Text>
      </Pressable>
    </View>
  );
};
    ```
## Modal component
 Modal is a screen that overlays the app content to provide important information or prompt the user for a decision . \ Since they are purposefully interruptive make sure you use them only when necessary
```
const App = () => {
  const [modalVisible, setModalVisible] = useState(false);

  const handlePress = () => {
    setModalVisible(!modalVisible);
  };

  return (
    <View style={styles.container}>
      <Pressable onPress={handlePress} style={styles.button}>
        <Text style={styles.text}>Open Modal</Text>
      </Pressable>

      <Modal
        animationType="slide" // Choose animation type: 'none', 'slide', 'fade'
        transparent={true}
        visible={modalVisible}
        onRequestClose={() => {
          setModalVisible(!modalVisible);
        }}
        presentationStyle="pageSheet" // Choose presentation style: 'fullScreen', 'pageSheet', 'formSheet'
      >
        <View style={styles.modalContainer}>
          <Text style={styles.modalText}>This is a modal</Text>
          <Pressable
            onPress={() => setModalVisible(!modalVisible)}
            style={({ pressed }) => [styles.button, pressed && styles.pressedButton]}
          >
            <Text style={styles.text}>Close Modal</Text>
          </Pressable>
        </View>
      </Modal>
    </View>
  );
};

```

## StausBar
 The StatusBar component allows you to control the applicatoins  status bar  \  the Status bar is the zone, typically at the top of the screen, that displays the current time, Wi-Fi and network information, battery level other status icons

```
     <StatusBar
        hidden={statusBarHidden}
        barStyle={statusBarStyle}
        backgroundColor={statusBarBackgroundColor}
        translucent={false}
      />
```
## ActivityIndicator
The ActivityIndicator component displays a circular loading indicator  \
 It is used to inform users about the status of ongoing processes, such as loading an app, submitting a form or saving updates

 ```
const App = () => {
  const [loading, setLoading] = useState(true);

  useEffect(() => {
    // Simulating an asynchronous task (e.g., fetching data)
    const fetchData = async () => {
      try {
        // Simulate data fetching delay (you can replace this with your actual data fetching logic)
        await new Promise(resolve => setTimeout(resolve, 2000));
        setLoading(false);
      } catch (error) {
        console.error('Error fetching data:', error);
        setLoading(false);
      }
    };

    fetchData();
  }, []);

  return (
    <View style={styles.container}>
      {loading ? (
        <ActivityIndicator size="large" color="#61dafb" />
      ) : (
        <View>
          <Text style={styles.text}>Data Loaded Successfully!</Text>
          {/* Your content here */}
        </View>
      )}
    </View>
  );
};
```

## Alert component
Alert launches an alert dialog iwth specific title and message \ Optionally, you  can also specify a list of buttons

```
const App = () => {
  const showAlert = () => {
    Alert.alert(
      'Alert Title',
      'This is the alert message.',
      [
        { text: 'Cancel', onPress: () => console.log('Cancel Pressed'), style: 'cancel' },
        { text: 'OK', onPress: () => console.log('OK Pressed') },
      ],
      { cancelable: false }
    );
  };

  return (
    <View style={styles.container}>
      <Text style={styles.text}>Click the button to show an alert:</Text>
      <Button title="Show Alert" onPress={showAlert} />
    </View>
  );
};
```

