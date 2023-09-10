Cambio la parte hardcoded di tutti i div precendti Creando un array che contiene i titoli delle categorie.

```jsx
 const categories = [

    {

      id: 1,

      title: 'Hats',

    },

    {

      id: 2,

      title: 'Jackets',

    },

    {

      id: 3,

      title: 'Sneackers',

    },

    {

      id: 4,

      title: 'Womens',

    },

    {

      id: 5,

      title: 'Sneakers',

    },

  ];
```

uso map() per estrapolare i dati dall'array

```jsx
return (

    <div className="categories-container">

      {categories.map(({title}) => (

        <div className="category-container">

          {<img className="background-image" /> }

          <div className="category-body-container">

            <h2>{title}</h2>

            <p>Shop Now</p>

          </div>

        </div>

      ))}

    </div>

  );

}
```
in questa react creaera tutti gli elementi presenti nell'array con il condice html inserito all'interno della funzione map()  ([[React ES6 Array Methods]])
