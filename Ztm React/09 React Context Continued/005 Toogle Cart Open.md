Terminata la presentazione del cart dropdown con if statement che rileva se il cart é aperto o chiuso inoltre creato il context per cart.

cart.context.jsx
```jsx
import { createContext, useState } from 'react';

  

export const CartContext = createContext({

  isCartOpen: false,

  setIsOpen: () => {},

});

  

export const CartProvider = ({ children }) => {

  const [isCartOpen, setIsCartOpen] = useState(false);

  const value = { isCartOpen, setIsCartOpen };

  return <CartContext.Provider value={value}>{children}</CartContext.Provider>;

};
```

controlla la pagina github per vedere i vari cambiamenti ecco il link.
https://github.com/tonyx92/my-app/commit/1dacb9cc9b5caeb3d9ed4bd549ee522aa5e5afb7
