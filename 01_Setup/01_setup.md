Fork and clone [this](https://github.com/JoinCODED/Demo-RN-M7-Forms) repository into your development folder.

1. We will create a simple registration form with validation, and discover whats the difference in handling input between React and React Native.

2. Let's create an input field component `components/input.js`.

```js
const Input = () => {};
```

3. This input will recive different props, and will be able to handle the input events.

```js
const Input = ({ label, iconName, error, onFocus = () => {} }) => {};
```

4. For now, let's just focus on those props.

5. Copy and paste those styles:

```js
const styles = StyleSheet.create({
  container: {
    marginBottom: 20,
  },
  label: {
    marginVertical: 5,
    fontSize: 14,
    color: '#BABBC3',
  },
  inputContainer: {
    height: 55,
    backgroundColor: '#F3F4FB',
    flexDirection: 'row',
    paddingHorizontal: 15,
    borderWidth: 0.5,
  },
  errorText: {
    color: 'red',
    fontSize: 12,
    marginTop: 7,
  },
  icon: {
    color: '#F47C7C',
    fontSize: 22,
    marginRight: 10,
  },
  input: {
    color: '#F47C7C',
    flex: 1,
  },
  passwordIcon: {
    color: '#F47C7C',
    fontSize: 22,
  },
});
```

6. Import required dependencies:

```js
import React, { useState } from 'react';
import { View, Text, TextInput, StyleSheet } from 'react-native';
import Icon from 'react-native-vector-icons/FontAwesome';
```

7. Let's create the input component:

```js
<View style={styles.container}>
  <Text style={styles.label}>{label}</Text>
  <View
    style={[
      styles.inputContainer,
      {
        borderColor: '#F47C7C',
        alignItems: 'center',
        borderRadius: 10,
      },
    ]}
  >
    <Icon name={iconName} style={styles.icon} />
    <TextInput
      autoCorrect={false}
      secureTextEntry={hidePassword}
      style={styles.input}
      {...props}
    />
  </View>
</View>
```

8. Now in `App.js` we can use the input component:

```js
          <Input
            iconName="envelope"
            label="Email"
            placeholder="Enter your email address"
          />

          <Input
            iconName="user"
            label="Full Name"
            placeholder="Enter your full name"
          />

          <Input
            iconName="phone"
            label="Phone Number"
            placeholder="Enter your phone no"
          />
```
