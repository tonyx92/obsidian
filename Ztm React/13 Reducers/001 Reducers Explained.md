![[vlcsnap-2023-02-01-17h06m10s153.png]]
nel caso di React utilizziamo useContext, useState, useEffect per modificare i dati , in questo caso quando aggiungiamo un elemento al carrello  items, count total cambiano tutti.

![[vlcsnap-2023-02-01-17h10m09s639.png]]

con Reducer abbiamo un oggetto cartReducer contenente i valori come sopra inoltre abbiamo un secondo oggetto chiamato Action contenente un type string e un payload any![[vlcsnap-2023-02-01-17h40m48s267.png]]

questa action reagisce a isCartOpen , non abbiamo bisogno di alcun payload in questo caso, cambierá quindi il valore da false a true.

![[vlcsnap-2023-02-01-17h43m24s826.png]]
in questo altro caso andiamo ad aggiungere a cart, nel payload ci saranno i valori/ oggetto delle istanze da modificare.
isCartOpen non viene utilizzato in questo caso.