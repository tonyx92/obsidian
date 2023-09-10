Creiamo una nuova cartella chiamata sign-up-form,component.jsx

```jsx
import { useState } from "react";

  

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

  

    const handleChange = (event) => {

        const {name, value} = event.target;

  

        setFormFields({...formFields, [name]: value});

    };

  

    return (

        <div>

            <h1>Sign up with your email and password</h1>

            <form onSubmit={() => {}}> {/* parte se solo tutti i campi sotto sono completati */}

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

abbiamo creato in render() le varie form di dati che verranno immagazzinati nel DB

utilizziammo [[React useState Hook]] per lo spostamento dei dati.