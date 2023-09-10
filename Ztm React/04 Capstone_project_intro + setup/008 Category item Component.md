inziamo a spostare glie elementi che compongono la app.js in cartelle components che verranno richioamate sulla pagina principale 


creiamo una cartella components e sucessivamente una sotto cartella category-item

inseriamo l'intero stile scss degli elementi della categoria in category-item.styles.scss

```scss
.category-container {

    min-width: 30%;

    height: 240px;

    flex: 1 1 auto;

    display: flex;

    align-items: center;

    justify-content: center;

    border: 1px solid black;

    margin: 0 7.5px 15px;

    overflow: hidden;

    &:hover {

      cursor: pointer;

      & .background-image {

        transform: scale(1.1);

        transition: transform 6s cubic-bezier(0.25, 0.45, 0.45, 0.95);

      }

      & .category-body-container {

        opacity: 0.9;

      }

    }

    &.large {

      height: 380px;

    }

    &:first-child {

      margin-right: 7.5px;

    }

    &:last-child {

      margin-left: 7.5px;

    }

    .background-image {

      width: 100%;

      height: 100%;

      background-size: cover;

      background-position: center;

    }

    .category-body-container {

      height: 90px;

      padding: 0 25px;

      display: flex;

      flex-direction: column;

      align-items: center;

      justify-content: center;

      border: 1px solid black;

      background-color: white;

      opacity: 0.7;

      position: absolute;

      h2 {

        font-weight: bold;

        margin: 0 6px 0;

        font-size: 22px;

        color: #4a4a4a;

      }

      p {

        font-weight: lighter;

        font-size: 16px;

      }

    }

  }
```


creiamo poi il file category-item.component.jsx

```jsx
import './category-item.styles.scss';

  

const CategoryItem = ({ category }) => {

  const { imageUrl, title } = category;

  return (

    <div className='category-container'>

      <div

        className='background-image'

        style={{

          backgroundImage: `url(${imageUrl})`,

        }}

      />

      <div className='category-body-container'>

        <h2>{title}</h2>

        <p>Shop Now</p>

      </div>

    </div>

  );

};

  

export default CategoryItem;
```

viene poi esportato in app.js 

```js
import CategoryItem from './components/category-item/category-item.component';

import './categories.stylers.scss';

const App = () => {

  

  const categories = [

    {

      "id": 1,

      "title": "hats",

      "imageUrl": "https://i.ibb.co/cvpntL1/hats.png"

    },

    {

      "id": 2,

      "title": "jackets",

      "imageUrl": "https://i.ibb.co/px2tCc3/jackets.png"

    },

    {

      "id": 3,

      "title": "sneakers",

      "imageUrl": "https://i.ibb.co/0jqHpnp/sneakers.png"

    },

    {

      "id": 4,

      "title": "womens",

      "imageUrl": "https://i.ibb.co/GCCdy8t/womens.png"

    },

    {

      "id": 5,

      "title": "mens",

      "imageUrl": "https://i.ibb.co/R70vBrQ/men.png"

    },

  ];

  

  return (

    <div className="categories-container">

      {categories.map((category) => (

        <CategoryItem key={category.id} category={category}/>

      ))}

    </div>

  );

}

  

export default App;
```

