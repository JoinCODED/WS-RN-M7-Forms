1. Create a state in `input.js`:

```js
const [hidePassword, setHidePassword] = useState(true);
```

2. Add an icon after the text input;

```js
{
  password && (
    <Icon
      name={hidePassword ? 'eye' : 'eye-slash'}
      style={styles.passwordIcon}
    />
  );
}
```

3. Clicking on this, should change our state to `false`;

```js
{
  password && (
    <Icon
      onPress={() => setHidePassword(!hidePassword)}
      name={hidePassword ? 'eye' : 'eye-slash'}
      style={styles.passwordIcon}
    />
  );
}
```

4. Lastly, change the `secureTextEntry` to our state:

```js
secureTextEntry = { hidePassword };
```
