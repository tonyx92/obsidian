creiamo il file products.context.jsx dove cambieremo la configurazione di tutti i fogli eseguiti precedentemente in modo che context tenga e fornisca tutti i dati relativi ai prodotti e li rigiri verso le altre parti dell'applicazione.
product.context.jsx = 
```jsx
import { createContext, useState } from 'react';

  
  

import PRODUCTS from '../shop-data.json';

  

export const ProductsContext = createContext({

    products: [],

});

  

export const ProductsProvider = ({children}) => {

    const [products,setProducts] = useState(PRODUCTS);

    const value = { products};

    return(

        <ProductsContext.Provider value={value}>{children}</ProductsContext.Provider>

    );

};
```

cambiamo ora quindi anche index.js dove l'inserimento di ProductProvider indica chi sará il child sottostante ad esso, cioé UserProvider.
```js
import React from 'react';

import ReactDOM from 'react-dom/client';

import { BrowserRouter } from 'react-router-dom';

import reportWebVitals from './reportWebVitals';

  
  

import App from './App';

import { UserProvider } from './context/user.context';

import { ProductsProvider } from './context/products.context';

  
  

import './index.scss';

  
  
  

const root = ReactDOM.createRoot(document.getElementById('root'));

root.render(

  <React.StrictMode>

    <BrowserRouter>

      <UserProvider>

        <ProductsProvider>

          <App />

        </ProductsProvider>

      </UserProvider>

    </BrowserRouter>

  </React.StrictMode>

);

  

// If you want to start measuring performance in your app, pass a function

// to log results (for example: reportWebVitals(console.log))

// or send to an analytics endpoint. Learn more: https://bit.ly/CRA-vitals

reportWebVitals();
```
infine modifichiamo il file shop.component.jsx con la nuova forma di inserimento dati
```jsx
import { useContext } from "react";

  

import { ProductsContext } from "../../context/products.context";

  

const Shop = () => {

    const {products} = useContext(ProductsContext);

    return (

        <div>

            {products.map(({id, name}) =>(

                <div key={id}>

                    <h1>{name}</h1>

                </div>

            ))}

        </div>

    )

}

  

export default Shop;
```

