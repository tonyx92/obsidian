Realizziamo un'altro metodo di sign-in che a differenza di popo up redirect a un altra pagina.
non verrá ;utilizzato nel progetto finale ma é per far capire che :
```js
const googleProvider = new GoogleAuthProvider();
```
puó essere usato per vari tipi di autenticazione.

resto del codice firebase.utility.js
```js
import { initializeApp } from 'firebase/app'; //init crea un'app instance per te, é un oggetto che ci permette di collegare le istanze

import {

    getAuth,

    signInWithRedirect,

    signInWithPopup,

    GoogleAuthProvider

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

  export const createUserDocumentFromAuth = async (userAuth) => {

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

                createdAt

            });

        } catch(error) {

            console.log('error creating the user', error.message);

        }

    }

    //if user data exist

    //return userdocref

    return userDocRef;

  };
```


resto del codice sign-in.jsx
```jsx
import { useEffect } from 'react'; //inserisco queste due import per redirect result salvare i dati

import { getRedirectResult } from 'firebase/auth';

  

import {

    auth,

    signInWithGooglePopup,

    signInWithGoogleRedirect,

    createUserDocumentFromAuth } from '../../utils/firebase/firebase.utils';

  
  

const SignIn = () => {

    //utilizzo useEffect perché voglio che il codice parta mentre sto montando array vuoto [], significa che la funzione va 1 volta

    useEffect(async () => {

        const response = await getRedirectResult(auth);

        if(response){

            const userDocRef = await createUserDocumentFromAuth(response);

        }

    }, []);

    const logGoogleUser = async () => {

        const {user} = await signInWithGooglePopup();

        const userDocRef = await createUserDocumentFromAuth(user);

    };

  

    return(

        <div>

         <h1>Sign in page</h1>

         <button onClick={logGoogleUser}>Sign in with Google Popup</button>

         <button onClick={signInWithGoogleRedirect}>Sign in with Google Redirect</button>

        </div>

    )

};

  
  
  

export default SignIn;
```