Iniziamo la creazione della pagina shop con carrello.

creiamo un file json in src chiamato shop-data.json con i seguenti contenuti
```json
[

    {

      "id": 1,

      "name": "Brown Brim",

      "imageUrl": "https://i.ibb.co/ZYW3VTp/brown-brim.png",

      "price": 25

    },

    {

      "id": 2,

      "name": "Blue Beanie",

      "imageUrl": "https://i.ibb.co/ypkgK0X/blue-beanie.png",

      "price": 18

    },

    {

      "id": 3,

      "name": "Brown Cowboy",

      "imageUrl": "https://i.ibb.co/QdJwgmp/brown-cowboy.png",

      "price": 35

    },

    {

      "id": 4,

      "name": "Grey Brim",

      "imageUrl": "https://i.ibb.co/RjBLWxB/grey-brim.png",

      "price": 25

    },

    {

      "id": 5,

      "name": "Green Beanie",

      "imageUrl": "https://i.ibb.co/YTjW3vF/green-beanie.png",

      "price": 18

    },

    {

      "id": 6,

      "name": "Palm Tree Cap",

      "imageUrl": "https://i.ibb.co/rKBDvJX/palm-tree-cap.png",

      "price": 14

    },

    {

      "id": 7,

      "name": "Red Beanie",

      "imageUrl": "https://i.ibb.co/bLB646Z/red-beanie.png",

      "price": 18

    },

    {

      "id": 8,

      "name": "Wolf Cap",

      "imageUrl": "https://i.ibb.co/1f2nWMM/wolf-cap.png",

      "price": 14

    },

    {

      "id": 9,

      "name": "Blue Snapback",

      "imageUrl": "https://i.ibb.co/X2VJP2W/blue-snapback.png",

      "price": 16

    }

  ]

```

all'interno della cartella routes creiamo un shop folder e creiamo il file shop.component.jsx
```jsx
import SHOP_DATA from '../../shop-data.json';

  

const Shop = () => {

    return (

        <div>

            {SHOP_DATA.map(({id, name}) =>(

                <div key={id}>

                    <h1>{name}</h1>

                </div>

            ))}

        </div>

    )

}

  

export default Shop;
```
inoltre modifichiamo app.js per inserire shop appena creato.

```jsx
import { Routes, Route } from 'react-router-dom';

  

import Home from './routes/home/home.component';

import Navigation from './routes/navigation/navigation.component';

import Authentication from './routes/authentication/authentication';

import Shop from './routes/shop/shop.component';

  
  
  
  
  

const App = () => {

  

 return (

  <Routes>

    <Route path= '/'element= { <Navigation /> } >

      <Route index element= {<Home />} />

      <Route path='shop' element= {<Shop />} /> //eccolo qua

      <Route path='auth' element= {<Authentication />} />  

    </Route>

  </Routes>

  );

};

  

export default App;
```

![[React shop.pdf]]
