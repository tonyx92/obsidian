![[vlcsnap-2023-01-14-17h31m35s030.png]]

nella pagina rules ci sono le regole per chi é autorizzato a effettuare CRUD

google creerá per noi alcuni documenti json quando effettuiamo un'autenticazione ma questi non verranno salvati nel DB.
Spetta a noi realizzare le parti all'interno del DB che terrá conto delle autentyicazioni con le chiavi primarie per gli utenti.

questo codice realizzato adesso stampa in console.log le chiavi dell'utente e verifica se é gia presente nel DB (al momento il DB non ha ancora una cartella user quindi la risposta === false , cioé non presentre).

firebase.utils.js : 
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

  

  const provider = new GoogleAuthProvider(); //ritorna l'istanza provider, é una class

  provider.setCustomParameters({

    prompt: "select_account"

  });

  

  export const auth = getAuth();// é sempre la stessa per la tua application

  export const signInWithGooglePopup = () => signInWithPopup(auth, provider);

  

  export const db = getFirestore();//punta direttamente al db all'interno della console

  export const createUserDocumentFromAuth = async (userAuth) => {

    const userDocRef = doc(db, 'users', userAuth.uid);

  

    console.log(userDocRef);

  

    const userSnapshot = await getDoc(userDocRef);

    console.log(userSnapshot);

    console.log(userSnapshot.exists()); //ci dice se dentro al nostro DB tale dato esiste giá

  

  };
```

pagina sign-in :

```jsx
import { signInWithGooglePopup, createUserDocumentFromAuth } from '../../utils/firebase/firebase.utils';

  
  

const SignIn = () => {

    const logGoogleUser = async () => {

        const {user} = await signInWithGooglePopup();

        createUserDocumentFromAuth(user);

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

