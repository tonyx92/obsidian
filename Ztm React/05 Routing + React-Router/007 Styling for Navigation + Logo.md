Aggiungiamo il logo svg in una cartela assets

aggiungiamo il scss della navigation

```scss
.navigation {

    height: 70px;

    width: 100%;

    display: flex;

    justify-content: space-between;

    margin-bottom: 25px;

    .logo-container {

      height: 100%;

      width: 70px;

      padding: 25px;

    }

    .nav-links-container {

      width: 50%;

      height: 100%;

      display: flex;

      align-items: center;

      justify-content: flex-end;

      .nav-link {

        padding: 10px 15px;

        cursor: pointer;

      }

    }

  }
```

Modifichiamo la paghina navigation.component.jsx
```jsx
import { Fragment } from "react";

import { Outlet, Link } from "react-router-dom"

  

import { ReactComponent as CrwnLogo } from '../../assets/083 crown.svg';

  

import './navigation.styles.scss';

  

const Navigation = () => {

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

          </div>

        </div>

        <Outlet />

      </Fragment>

    )

  }

  

  export default Navigation;
```

inoltre modifichiamo la cartella index.scss che controlla gli elemnti di tutta la app .
togliamo la colorazione dei testi link e aggiungiamo box-sizing: border-box a tutti gli elementi.   https://www.w3schools.com/css/css3_box-sizing.asp

```scss
body {

  margin: 0;

  font-family: 'Bebas Neue', sans-serif;

  -webkit-font-smoothing: antialiased;

  -moz-osx-font-smoothing: grayscale;

}

  

code {

  font-family: source-code-pro, Menlo, Monaco, Consolas, 'Courier New',

    monospace;

}

  

a{

  text-decoration: none;

  color: black;

}

  

*{

  box-sizing: border-box;

}
```