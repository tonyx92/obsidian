per implementare sign out andiamo a inserire in navigation.component.jsx il seguente codice:
```jsx
import { Fragment, useContext } from "react";

import { Outlet, Link } from "react-router-dom"

  

import { ReactComponent as CrwnLogo } from '../../assets/083 crown.svg';

import { UserContext } from "../../context/user.context";

  

import { signOutUser } from "../../utils/firebase/firebase.utils";

  

import './navigation.styles.scss';

  

const Navigation = () => {

  const { currentUser, setCurrentUser } = useContext(UserContext);

  

  const signOutHandler = async () => {

    await signOutUser();

    setCurrentUser(null);

  }

  

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

            {

              currentUser ? (

                <span className="nav-link" onClick={signOutUser}> SIGN OUT </span>

                ) : (<Link className="nav-link" to='/auth'>

                Sign In

            </Link>

              )

            }

          </div>

        </div>

        <Outlet />

      </Fragment>

    )

  }

  

  export default Navigation;
```

in cui si dice che lo stato di user quando viene cliccato log out divieno null.
nell'html si crea un if else in cui il rendering della DOM cambia in base se currentUser contiene dei dati altrimenti ritorna sign in.