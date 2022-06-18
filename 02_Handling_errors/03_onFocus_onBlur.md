1. We don't want the error to stay there for ever, we will clear it when the user clicks on the field.

2. Create a state in `Input.js`:

```js
const [isFocused, setIsFocused] = useState(false);
```

3. On each field, pass `onFocus`, and call `handleError` and pass `null` to it to clear the error.

```js
         <Input
            onChangeText={(text) => handleOnchange(text, 'email')}
            onFocus={() => handleError(null, 'email')}
            iconName="envelope"
            label="Email"
            placeholder="Enter your email address"
            error={errors.email}
          />

          <Input
            onChangeText={(text) => handleOnchange(text, 'fullname')}
            onFocus={() => handleError(null, 'fullname')}
            iconName="user"
            label="Full Name"
            placeholder="Enter your full name"
            error={errors.fullname}
          />

          <Input
            onChangeText={(text) => handleOnchange(text, 'phone')}
            onFocus={() => handleError(null, 'phone')}
            iconName="phone"
            label="Phone Number"
            placeholder="Enter your phone no"
            error={errors.phone}
          />
```

4. In `Input.js` Let's color the border if the input is focused or if there's and error.

```js
      <View
        style={[
          styles.inputContainer,
          {
            borderColor: error ? 'red' : isFocused ? '#F47C7C' : '#F3F4FB',
            alignItems: 'center',
            borderRadius: 10,
          },
        ]}
      >
```

5. And on the `onFocus` prop of the `TextInput` we call `setIsFocused` and pass `true` to it and also call the `onFocus` that we passed.

```js
<TextInput
  autoCorrect={false}
  onFocus={() => {
    onFocus();
    setIsFocused(true);
  }}
  style={styles.input}
  {...props}
/>
```

6. We will also pass an `onBlur` prop to the `TextInput` to call `setIsFocused` and pass `false` to it.

```js
    onBlur={() => setIsFocused(false)}
```
