
continiamo a modulare l'apllicazione aggiungendo una cartella Directory all'interno di components.

inseriamo directory.styles.scss

```scss
.directory-container {

    width: 100%;

    display: flex;

    flex-wrap: wrap;

    justify-content: space-between;

  }
```

inseriamo directory.component.jsx

```jsx
import CategoryItem from '../category-item/category-item.component';

  

import './directory.styles.scss';

  
  

const Directory = ({categories}) => {

    return (

        <div className="directory-container">

          {categories.map((category) => (

            <CategoryItem key={category.id} category={category}/>

          ))}

        </div>

      );

}

  

export default Directory;
```

modifichiamo app.js in modo che ritorni directory:

```jsx
return <Directory categories={categories} />
```

usiamo git per inserire il progetto sul mio profilo github [[Git Commit]]

```bash
git init
git add -A
git commit -m 'primo inserimento'
git push
```

