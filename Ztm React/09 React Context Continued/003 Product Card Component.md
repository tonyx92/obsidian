Creiamo i seguenti file con anche gli stili scss :
product-card.jsx
```jsx
import './product-card.styles.scss';

  

import Button from '../button/button.component';

  

const ProductCard = ({product}) => {

    const { name, price, imageUrl } = product;

    return (<div className='product-card-container'>

        <img src={imageUrl} alt={`${name}`}/>

        <div className='footer'>

            <span className='name'>{name} </span>

            <span className='price'>{price} </span>

        </div>

     <Button buttonType='inverted'>add to cart</Button>

    </div>)

};

  

export default ProductCard;
```

product-cart.styles.scss
```scss
.product-card-container {

    width: 100%;

    display: flex;

    flex-direction: column;

    height: 350px;

    align-items: center;

    position: relative;

    img {

      width: 100%;

      height: 95%;

      object-fit: cover;

      margin-bottom: 5px;

    }

    button {

      width: 80%;

      opacity: 0.7;

      position: absolute;

      top: 255px;

      display: none;

    }

    &:hover {

      img {

        opacity: 0.8;

      }

      button {

        opacity: 0.85;

        display: flex;

      }

    }

    .footer {

      width: 100%;

      height: 5%;

      display: flex;

      justify-content: space-between;

      font-size: 18px;

      .name {

        width: 90%;

        margin-bottom: 15px;

      }

      .price {

        width: 10%;

      }

    }

  }
```

modifichiamo product compoinent per utilizzare product card come base html per i dati
```jsx
import { useContext } from "react";

  

import { ProductsContext } from "../../context/products.context";

import ProductCard from "../../components/product-card/product-card.component";

import "./shop.styles.scss";

  

const Shop = () => {

    const {products} = useContext(ProductsContext);

    return (

        <div className="products-container">

            {products.map((product) =>(

                <ProductCard key={product.id} product={product}/>

            ))}

        </div>

    )

}

  

export default Shop;
```
aggiungiamo anche uno style per shop.styles.scss
```scss
.products-container {

    display: grid;

    grid-template-columns: repeat(4, 1fr);

    column-gap: 10px;

    row-gap: 50px;

}
```

abbiamo cosi ottenuto le nostre card di prododtti.
![[cards.pdf]]