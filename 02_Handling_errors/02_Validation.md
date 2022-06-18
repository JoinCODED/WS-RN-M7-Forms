1. Create a function that will validate the inputs.

```js
const validate = async () => {};
```

2. We will close the user keyboard first.

```js
const validate = async () => {
  Keyboard.dismiss();
};
```

3. Then we will iterate over the inputs and validate them using `yup.validateAt` to validate a single field at a time.

```js
for (const field in inputs) {
  try {
    await schema.validateAt(field, inputs);
  } catch (error) {
    console.log(error.errors[0]);
  }
}
```

4. This will return an array of errors, we need the first error in the array.

5. Let's create a `handleError` function similar to the one we did in the previous section.

```js
const handleError = (error, input) => {
  setErrors((prevState) => ({ ...prevState, [input]: error }));
};
```

6. In your `validate` function, use `handleError` set a key value pair of the field name and the message.

```js
const validate = async () => {
  Keyboard.dismiss();
  for (const field in inputs) {
    try {
      await schema.validateAt(field, inputs);
    } catch (error) {
      handleError(error.errors[0], field);
    }
  }
};
```

7. Now on each field, pass the error message:

```js
          <Input
            onChangeText={(text) => handleOnchange(text, 'email')}
            iconName="envelope"
            label="Email"
            placeholder="Enter your email address"
            error={errors.email}
          />

          <Input
            onChangeText={(text) => handleOnchange(text, 'fullname')}
            iconName="user"
            label="Full Name"
            placeholder="Enter your full name"
            error={errors.fullname}
          />

          <Input
            onChangeText={(text) => handleOnchange(text, 'phone')}
            iconName="phone"
            label="Phone Number"
            placeholder="Enter your phone no"
            error={errors.phone}
          />
```

8. Assign the `validate` function to the `button`.

```js
<Button title="Register" onPress={validate} />
```

9. Finally, add the error message in `Input.js`:

```js
{
  error && <Text style={styles.errorText}>{error}</Text>;
}
```
