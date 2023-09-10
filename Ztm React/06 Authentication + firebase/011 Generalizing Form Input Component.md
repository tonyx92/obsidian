Abbiamo terminato la costruzione di sign-in con email, aggiunti acnhe metodi scss e tutti i collegamenti necessari con firebase.

sign-up-form.component.jsx
```jsx
import { useState } from 'react';

  

import FormInput from '../form-input/form-input.component';

//import Button from '../button/button.component';

  

import {

  createAuthUserWithEmailAndPassword,

  createUserDocumentFromAuth,

} from '../../utils/firebase/firebase.utils';

  

//import './sign-up-form.styles.scss';

  

const defaultFormFields = {

  displayName: '',

  email: '',

  password: '',

  confirmPassword: '',

};

  

const SignUpForm = () => {

  const [formFields, setFormFields] = useState(defaultFormFields);

  const { displayName, email, password, confirmPassword } = formFields;

  

  const resetFormFields = () => {

    setFormFields(defaultFormFields);

  };

  

  const handleSubmit = async (event) => {

    event.preventDefault();

  

    if (password !== confirmPassword) {

      alert('passwords do not match');

      return;

    }

  

    try {

      const { user } = await createAuthUserWithEmailAndPassword(

        email,

        password

      );

  

      await createUserDocumentFromAuth(user, { displayName });

      resetFormFields();

    } catch (error) {

      if (error.code === 'auth/email-already-in-use') {

        alert('Cannot create user, email already in use');

      } else {

        console.log('user creation encountered an error', error);

      }

    }

  };

  

  const handleChange = (event) => {

    const { name, value } = event.target;

  

    setFormFields({ ...formFields, [name]: value });

  };

  

  return (

    <div className='sign-up-container'>

      <h2>Don't have an account?</h2>

      <span>Sign up with your email and password</span>

      <form onSubmit={handleSubmit}>

        <FormInput

          label='Display Name'

          type='text'

          required

          onChange={handleChange}

          name='displayName'

          value={displayName}

        />

  

        <FormInput

          label='Email'

          type='email'

          required

          onChange={handleChange}

          name='email'

          value={email}

        />

  

        <FormInput

          label='Password'

          type='password'

          required

          onChange={handleChange}

          name='password'

          value={password}

        />

  

        <FormInput

          label='Confirm Password'

          type='password'

          required

          onChange={handleChange}

          name='confirmPassword'

          value={confirmPassword}

        />

        <button type='submit'>Sign Up</button>

      </form>

    </div>

  );

};

  

export default SignUpForm;
```

form-input.component.jsx
```jsx
import './form-input.styles.scss';

  

const FormInput = ({ label, ...otherProps }) => {

  return (

    <div className='group'>

      <input className='form-input' {...otherProps} />

      {label && (

        <label

          className={`${

            otherProps.value.length ? 'shrink' : ''

          } form-input-label`}

        >

          {label}

        </label>

      )}

    </div>

  );

};

  

export default FormInput;
```

form-input.styles.scss
```scss
$sub-color: grey;

$main-color: black;

  

@mixin shrinkLabel {

  top: -14px;

  font-size: 12px;

  color: $main-color;

}

  

.group {

  position: relative;

  margin: 45px 0;

  

  .form-input {

    background: none;

    background-color: white;

    color: $sub-color;

    font-size: 18px;

    padding: 10px 10px 10px 5px;

    display: block;

    width: 100%;

    border: none;

    border-radius: 0;

    border-bottom: 1px solid $sub-color;

    margin: 25px 0;

  

    &:focus {

      outline: none;

    }

  

    &:focus ~ .form-input-label {

      @include shrinkLabel();

    }

  }

  

  input[type='password'] {

    letter-spacing: 0.3em;

  }

  

  .form-input-label {

    color: $sub-color;

    font-size: 16px;

    font-weight: normal;

    position: absolute;

    pointer-events: none;

    left: 5px;

    top: 10px;

    transition: 300ms ease all;

  

    &.shrink {

      @include shrinkLabel();

    }

  }

}
```