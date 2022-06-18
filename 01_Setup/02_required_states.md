1. In `app.js` we will create a state that hold our form values.

```js
const [inputs, setInputs] = useState({
  email: '',
  fullname: '',
  phone: '',
});
```

2. Then, like we used to do in react, we will create a `handleChange` function that will be called when the user changes the value of the input.

```js
const handleOnchange = (text, input) => {
  setInputs((prevState) => ({ ...prevState, [input]: text }));
};
```

3. Our first difference will be the `onChange` property, in react native, we use `onChangeText` instead of `onChange`.

```js
<Input
            onChangeText={(text) => handleOnchange(text, 'email')}
            iconName="envelope"
            label="Email"
            placeholder="Enter your email address"
          />

          <Input
            onChangeText={(text) => handleOnchange(text, 'fullname')}
            iconName="user"
            label="Full Name"
            placeholder="Enter your full name"
          />

          <Input
            onChangeText={(text) => handleOnchange(text, 'phone')}
            iconName="phone"
            label="Phone Number"
            placeholder="Enter your phone no"
          />
```
