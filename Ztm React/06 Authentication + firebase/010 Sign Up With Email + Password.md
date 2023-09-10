firebase.utils.js

```js
import { initializeApp } from 'firebase/app'; //init crea un'app instance per te, é un oggetto che ci permette di collegare le istanze

import {

    getAuth,

    signInWithRedirect,

    signInWithPopup,

    GoogleAuthProvider,

    createUserWithEmailAndPassword

} from 'firebase/auth';

import {

    getFirestore,

    doc, //ritorna documenti all'interno di firebase

    getDoc,//getting the document data

    setDoc//setting the document data

} from 'firebase/firestore';

  
  

// Your web app's Firebase configuration

//generata dalla pagina web firebase

const firebaseConfig = {

    apiKey: "AIzaSyBl09vs-Hqax43e1CPNCPz3-rE1Y8kNlfg",

    authDomain: "crwn-clothing-db-25513.firebaseapp.com",

    projectId: "crwn-clothing-db-25513",

    storageBucket: "crwn-clothing-db-25513.appspot.com",

    messagingSenderId: "184633970335",

    appId: "1:184633970335:web:454f00b2fd85d745b4dcaa"

  };

  // Initialize Firebase

  const firebaseApp = initializeApp(firebaseConfig);

  

  const googleProvider = new GoogleAuthProvider(); //ritorna l'istanza provider, é una class

  googleProvider.setCustomParameters({

    prompt: "select_account"

  });

  

  export const auth = getAuth();// é sempre la stessa per la tua application

  export const signInWithGooglePopup = () =>

    signInWithPopup(auth, googleProvider);//registrazione con google sign-in

  export const signInWithGoogleRedirect = () =>

    signInWithGoogleRedirect(auth, googleProvider);//registrazione tramite google reindirizzandomi in un'altra pagina/tab

  

  export const db = getFirestore();//punta direttamente al db all'interno della console

  export const createUserDocumentFromAuth = async (

    userAuth,

    additionalInformation = {}

  ) => {

    if(!userAuth) return;

  

    const userDocRef = doc(db, 'users', userAuth.uid);

  

    const userSnapshot = await getDoc(userDocRef);

      //if userdata does not exist

        //create / set document with the data from userAuth in my collection

    if(!userSnapshot.exists()){

        const { displayName , email } = userAuth;

        const createdAt = new Date();

  

        try {

            await setDoc(userDocRef, {

                displayName,

                email,

                createdAt,

                ...additionalInformation,

            });

        } catch(error) {

            console.log('error creating the user', error.message);

        }

    }

    //if user data exist

    //return userdocref

    return userDocRef;

  };

  

  export const createAuthUserWithEmailAndPassword = async (email, password) => {

    if(!email || !password) return;

  

    createAuthUserWithEmailAndPassword(auth, email, password)

  

  }
```


sign-up.component.jsx
```jsx
import { useState } from "react";

  

import { createAuthUserWithEmailAndPassword, createUserDocumentFromAuth } from "../../utils/firebase/firebase.utils";

  

const defaultFormFields = { //questo oggetto viene poi passato a useState per essewre gestito

    diplayName: '',

    email: '',

    password: '',

    confirmPassword: ''

}

  

const SignUpForm = () => {

  

    const[formFields, setFormFields] = useState(defaultFormFields);

    const { displayName, email, password, confirmPassword} = formFields;//destructoring i 4 valori dell'oggetto e li rendo delle const per usarli quando mi servono

  

    console.log(formFields);

  

    const resetFormFields = () => {

        setFormFields(defaultFormFields);

    }

  

    const handleSubmit = async (event) => {

        event.preventDefault();//tutto cio che avviene nella form lo gestiamo noi

        if(password !== confirmPassword) {

            alert("password doesn't match");

            return;

        }

  

        try{

            const {user} = await createAuthUserWithEmailAndPassword(

                email,

                 password

            );

  

            await createUserDocumentFromAuth(user, {displayName});

            resetFormFields();

  

        }catch(error){

            if(error.code === 'auth/email-already-in-use'){

                alert('Cannot create user, email already in use');

            }

            console.log("user creation encountered an error", error);

        }

    };

  

    const handleChange = (event) => {

        const {name, value} = event.target;

  

        setFormFields({...formFields, [name]: value});

    };

  

    return (

        <div>

            <h1>Sign up with your email and password</h1>

            <form onSubmit={handleSubmit}> {/* parte se solo tutti i campi sotto sono completati */}

                <label>Display name</label>

                <input type='text' required onChange={handleChange} name='diplayName' value={displayName} />

                <label>Email</label>

                <input type="email" required onChange={handleChange} name='email' value={email}/>

                <label>Password</label>

                <input type="password" required onChange={handleChange} name='password'value={password}/>

                <label>Confirm Password</label>

                <input type="password" required onChange={handleChange} name='confirmPassword' value={confirmPassword}/>

                <button type="submit">Sign Up</button>

            </form>

        </div>

    );

};

  

export default SignUpForm;
```