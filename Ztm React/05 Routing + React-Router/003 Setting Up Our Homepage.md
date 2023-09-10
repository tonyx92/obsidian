
importiamo browserRouter in index.js


```js
import { BrowserRouter } from 'react-router-dom';
```

utilizziamo le tag browserRouter per incapsulare l'intra nosta app

```js
const root = ReactDOM.createRoot(document.getElementById('root'));

root.render(

  <React.StrictMode>

    <BrowserRouter>

      <App />

    </BrowserRouter>

  </React.StrictMode>

);
```


creiamo un folder chiamato routes in src dove inseriremo tutti gli elemnti delle routes persistenti.

in app.js 

```jsx
import { Routes, Route } from 'react-router-dom';

  
  

import Home from './routes/home/home.component';

  
  
  

const App = () => {

  

 return (

  <Routes>

    <Route path='/' element= {<Home />} />  

  </Routes>

  );

};

  

export default App;
```

importo router, importo la home

all'interno della funzione return () inserisco routes e route con path = / che significa la home page url e element={ } é il modulo che voglio venga renderizzato quando mi trovo all'interno del determianto path precedente.