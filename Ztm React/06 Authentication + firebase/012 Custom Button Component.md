button.component.jsx
```jsx
import "./button.styles.scss";

  
  

// creiamo un variabile che ci permette di avere tre stili di button differenti

const BUTTON_TYPE_CLASSES ={

    google: 'google-sign-in',

    inverted: 'inverted'

}

  
  

const Button = ({children, buttonType, ...otherProps}) =>{

    return (

        <button className={`button-container ${BUTTON_TYPE_CLASSES[buttonType]}`}

            {...otherProps}

        >

            {children}

        </button>

    );

};

  

export default Button;
```

button.styles.scss
```scss
.button-container {

    min-width: 165px;

    width: auto;

    height: 50px;

    letter-spacing: 0.5px;

    line-height: 50px;

    padding: 0 35px 0 35px;

    font-size: 15px;

    background-color: black;

    color: white;

    text-transform: uppercase;

    font-family: 'Open Sans Condensed';

    font-weight: bolder;

    border: none;

    cursor: pointer;

    display: flex;

    justify-content: center;

    &:hover {

      background-color: white;

      color: black;

      border: 1px solid black;

    }

    &.google-sign-in {

      background-color: #4285f4;

      color: white;

      &:hover {

        background-color: #357ae8;

        border: none;

      }

    }

    &.inverted {

      background-color: white;

      color: black;

      border: 1px solid black;

      &:hover {

        background-color: black;

        color: white;

        border: none;

      }

    }

  }
```

sign-up-form.component.jsx
```jsx
import { useState } from 'react';

  

import FormInput from '../form-input/form-input.component';

import Button from '../button/button.component';

  

import {

  createAuthUserWithEmailAndPassword,

  createUserDocumentFromAuth,

} from '../../utils/firebase/firebase.utils';

  

import './sign-up-form.styles.scss';

  

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

        <Button buttonType='inverted' type='submit'>Sign Up</Button>

      </form>

    </div>

  );

};

  

export default SignUpForm;
```
