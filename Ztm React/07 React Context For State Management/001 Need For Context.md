![[vlcsnap-2023-01-18-21h58m14s273.png]]
nel nostro albero app, app.js si occuperá di passare user data agli altri childs.

![[vlcsnap-2023-01-18-22h00m06s485.png]]
i nodi arancioni si occupano di trasportare i dati da sign in/up a profile,returns e history.
le passiamo con le props detto props drilling. [[React props]]

noi invece useremo un'altro metodo

![[vlcsnap-2023-01-18-22h05m23s383.png]]
inseriremo ad esempio i dati user data in una zona esterna l'albero app![[vlcsnap-2023-01-18-22h06m28s078.png]]
e li passeremo direttamente a chi ne fa richiesta.