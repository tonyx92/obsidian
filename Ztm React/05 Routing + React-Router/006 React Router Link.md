Abbiamo  utilizzato i metodi link per creare link che trasportano in un altro Url utilizzando React router.

Abbiamo anche utilizzato Fragment from react per creare delle divisioni che non vengono messe nella DOM a differenza di usare 
https://beta.reactjs.org/learn/escape-hatches
```html
<div></div>

usiamo
<fragment></fragment>
```

Resto del codice: 

```jsx
import { Fragment } from "react";

  

import { Outlet, Link } from "react-router-dom"

  

const Navigation = () => {

    return (

      <Fragment>

        <div className="navigation">

          <Link className="logo-container" to='/'>

            <div>Logo</div>

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