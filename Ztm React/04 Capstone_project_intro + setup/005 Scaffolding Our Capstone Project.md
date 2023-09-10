usiamo create react app per inizializzare il progetto

lo chiamo eshop-vestiti

Cambio la funzione in app.js in arrow function es6 

```jsx
const App = () => {

  return    <div>Hello World</div>

}
```


creo i container per le immagini e la suddivisione della impaginazione.
verranno stilizzati sucessivamente con SASS .

```jsx
const App = () => {

  return (

    <div className="categories-container">

      <div className="category-container">

        {/*<img /> é commentata perché l'immagine verrá aggiunta in seguito*/}

        <div className="category-body-container">

          <h2>Hats</h2>

          <p>Shop Now</p>

        </div>

      </div>

      <div className="category-container">

        {/*<img /> é commentata perché l'immagine verrá aggiunta in seguito*/}

        <div className="category-body-container">

          <h2>Jackets</h2>

          <p>Shop Now</p>

        </div>

      </div>

      <div className="category-container">

        {/*<img /> é commentata perché l'immagine verrá aggiunta in seguito*/}

        <div className="category-body-container">

          <h2>Sneakers</h2>

          <p>Shop Now</p>

        </div>

      </div>

      <div className="category-container">

        {/*<img /> é commentata perché l'immagine verrá aggiunta in seguito*/}

        <div className="category-body-container">

          <h2>Womens</h2>

          <p>Shop Now</p>

        </div>

      </div>

      <div className="category-container">

        {/*<img /> é commentata perché l'immagine verrá aggiunta in seguito*/}

        <div className="category-body-container">

          <h2>Mens</h2>

          <p>Shop Now</p>

        </div>

      </div>

    </div>

  );

}

  

export default App;
```

![[Immagine 2023-01-11 143153.png]]
