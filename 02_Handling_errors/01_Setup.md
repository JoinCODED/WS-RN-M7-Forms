1. We will use `yup` to validate the inputs.

```shell
npm install --save yup
```

```js
import * as yup from 'yup';
```

2. Create a schema that will validate the inputs.

```js
let schema = yup.object().shape({
  fullname: yup.string().min(3).required(),
  phone: yup.string().required(),
  email: yup.string().email().required(),
});
```

3. Create a state that will hold the errors.

```js
const [errors, setErrors] = useState({});
```
