creiamo uno 'Strato in navigation che terrá i dati user'.
per fare ció usiamo le hooks [[React useContext Hook]] e [[React useState Hook]]


creiamo una nuova cartella in src chiamata context in cui useremo le regole hooks in user.context.jsx : 
```jsx
import { createContext, useState } from 'react';

  
  

//as the actual value you want to access

export const UserContext = createContext({

    currentUser: null,

    setCurrentUser: () => null,

});

  
  

export const UserProvider = ({children}) => {

    const [currentUser, setCurrentUser] = useState(null);

    const value = {currentUser, setCurrentUser};

  
  

    return <UserContext.Provider value={value}>{children}</UserContext.Provider>

}
```

inoltre modifichiamo sia sign-in che navigation per il trasporto delle info user.

sign-in modifiche : 
```jsx
import { useState, useContext} from 'react';

  

import FormInput from '../form-input/form-input.component';

import Button from '../button/button.component';

  

import { UserContext } from '../../context/user.context'; //questo appena aggiunto

  

import {

  signInWithGooglePopup,

  createUserDocumentFromAuth,

  signInAuthUserWithEmailAndPassword,

} from '../../utils/firebase/firebase.utils';

  

import './sign-in-form.styles.scss';

  

const defaultFormFields = {

  email: '',

  password: '',

};

  

const SignInForm = () => {

  const [formFields, setFormFields] = useState(defaultFormFields);

  const { email, password } = formFields;

  

  const { setCurrentUser } = useContext(UserContext);

  

  const resetFormFields = () => {

    setFormFields(defaultFormFields);

  };

  

  const signInWithGoogle = async () => {

    const { user } = await signInWithGooglePopup();

    await createUserDocumentFromAuth(user);

  };

  

  const handleSubmit = async (event) => {

    event.preventDefault();

  

    try {
		//cambiato con user
      const { user } = await signInAuthUserWithEmailAndPassword(

        email,

        password

      );

      setCurrentUser(user);

  

      resetFormFields();

    } catch (error) {

      switch (error.code) {

        case 'auth/wrong-password':

          alert('incorrect password for email');

          break;

        case 'auth/user-not-found':

          alert('no user associated with this email');

          break;

        default:

          console.log(error);

      }

    }

  };

  

  const handleChange = (event) => {

    const { name, value } = event.target;

  

    setFormFields({ ...formFields, [name]: value });

  };

  

  return (

    <div className='sign-up-container'>

      <h2>Already have an account?</h2>

      <span>Sign in with your email and password</span>

      <form onSubmit={handleSubmit}>

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

        <div className='buttons-container'>

          <Button type='submit'>Sign In</Button>

          <Button type='button' buttonType='google' onClick={signInWithGoogle}>

            Google sign in

          </Button>

        </div>

      </form>

    </div>

  );

};

  

export default SignInForm;
```


navigation.component.jsx importiamo  usercontext e creiamo una variabile contenente dati utente
```jsx
import { Fragment, useContext } from "react";

import { Outlet, Link } from "react-router-dom"

  

import { ReactComponent as CrwnLogo } from '../../assets/083 crown.svg';

import { UserContext } from "../../context/user.context";

  

import './navigation.styles.scss';

  

const Navigation = () => {

  const { currentUser } = useContext(UserContext);

  

    return (

      <Fragment>

        <div className="navigation">

          <Link className="logo-container" to='/'>

            <CrwnLogo className="logo" />

          </Link>

          <div className="links-container">

            <Link className="nav-link" to='/shop'>

                SHOP

            </Link>

            <Link className="nav-link" to='/auth'>

                Sign In

            </Link>

          </div>

        </div>

        <Outlet />

      </Fragment>

    )

  }

  

  export default Navigation;
```


infine incapsuliamo app in app.js per il trasporto

```js
import { Routes, Route } from 'react-router-dom';

  

import Home from './routes/home/home.component';

import Navigation from './routes/navigation/navigation.component';

import Authentication from './routes/authentication/authentication';

  
  
  
  
  
  

const App = () => {

  

 return (

  <Routes>

    <Route path= '/'element= { <Navigation /> } >

      <Route index element= {<Home />} />

      <Route path='auth' element= {<Authentication />} />  

    </Route>

  </Routes>

  );

};

  

export default App;
```

