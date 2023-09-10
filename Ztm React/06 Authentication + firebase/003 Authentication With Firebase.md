Creaiamo il collegamento al nostro sito web e la piattaforma DB firebase.
Creiamoi anche una sotto cartella in src chiamata utils per inserire tutti i dati e modalita di collegamento a firebase.

```js
import { initializeApp } from 'firebase/app'; //init crea un'app instance per te, é un oggetto che ci permette di collegare le istanze

import {

    getAuth,

    signInWithRedirect,

    signInWithPopup,

    GoogleAuthProvider

} from 'firebase/auth';

  
  

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

  

  const provider = new GoogleAuthProvider(); //ritorna l'istanza provider, é una class

  provider.setCustomParameters({

    prompt: "select_account"

  });

  

  export const auth = getAuth();// é sempre la stessa per la tua application

  export const signInWithGooglePopup = () => signInWithPopup(auth, provider);
```

Google docs da leggere nel caso ====>  https://firebase.google.com/docs/auth/web/google-signin#web-version-9_3

modifichiamo la pagina sign-in per creare un bottone di sign-in with google.

```jsx
import { signInWithGooglePopup } from '../../utils/firebase/firebase.utils';

  

const SignIn = () => {

    const logGoogleUser = async () => {

        const response = await signInWithGooglePopup();

        console.log(response);

    }

  

    return(

        <div>

         <h1>Sign in page</h1>

         <button onClick={logGoogleUser}>

            Sign in with Google Popup

         </button>

        </div>

    )

};

  
  
  

export default SignIn;
```




