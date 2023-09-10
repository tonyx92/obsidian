Aggiungiamo il dropdown del cart e il suo stile e lo aggiungiamo in navigation

cart-dropdown.jsx
```jsx
import React from 'react';

  

import Button from '../button/button.component';

  

import './cart-dropdown.styles.scss';

  

const CartDropdown = () => {

    <div className='cart-dropdown-container'>

        <div className='cart-items' />

        <Button>GO TO CHECK OUT</Button>

    </div>

  

}

  

export default CartDropdown;
```

scss
```scss
.cart-dropdown-container {

  position: absolute;

  width: 240px;

  height: 340px;

  display: flex;

  flex-direction: column;

  padding: 20px;

  border: 1px solid black;

  background-color: white;

  top: 90px;

  right: 40px;

  z-index: 5;

  

  .empty-message {

    font-size: 18px;

    margin: 50px auto;

  }

  

  .cart-items {

    height: 240px;

    display: flex;

    flex-direction: column;

    overflow: scroll;

  }

  

  button {

    margin-top: auto;

  }

}
```

pezzo aggiunto a navigation oltre all'import
```jsx
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

            {

              currentUser ? (

                <span className="nav-link" onClick={signOutUser}> SIGN OUT </span>

                ) : (<Link className="nav-link" to='/auth'>

                Sign In

            </Link>

              )}

            <CartIcon />

          </div>

          <CartDropdown /> //======>  questo qua!!!!!

        </div>

        <Outlet />

      </Fragment>

    )

  }
```
