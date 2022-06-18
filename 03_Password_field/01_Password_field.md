1. Add another field to the form.

```js
<Input
  onChangeText={(text) => handleOnchange(text, 'password')}
  onFocus={() => handleError(null, 'password')}
  iconName="key"
  label="Password"
  placeholder="Enter your password"
  error={errors.password}
/>
```

```js
let schema = yup.object().shape({
  fullname: yup.string().min(3).required(),
  phone: yup.string().required(),
  email: yup.string().email().required(),
  password: yup.string().required().min(6),
});
```

```js
const [inputs, setInputs] = useState({
  email: '',
  fullname: '',
  phone: '',
  password: '',
});
```

2. One extra step for the password field, we will pass `password` as a prop.

```js
<Input
  onChangeText={(text) => handleOnchange(text, 'password')}
  onFocus={() => handleError(null, 'password')}
  iconName="key"
  label="Password"
  placeholder="Enter your password"
  error={errors.password}
  password
/>
```

3. Recive this prop in the `Input.js` file. and set the `secureTextEntry` to `true`.

```js
<TextInput
  autoCorrect={false}
  onFocus={() => {
    onFocus();
    setIsFocused(true);
  }}
  onBlur={() => setIsFocused(false)}
  secureTextEntry={password}
  style={styles.input}
/>
```
