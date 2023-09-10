![[vlcsnap-2023-01-19-17h28m15s683.png]]
esempio di asyncronous stream in cui abbiamo una sequenza di click su di un bottone a intervalli di tempo irregolari.

Abbiamo poi una class Listener con tre metodi che esegue delle azioni in base a qualcosa: 
![[vlcsnap-2023-01-19-17h30m25s225.png]]

![[vlcsnap-2023-01-19-17h31m11s163.png]]
subscribe significa iniziare ad ascoltare quello che sta succedendo nello stream![[vlcsnap-2023-01-19-17h32m42s090.png]]
![[vlcsnap-2023-01-19-17h32m55s175.png]]
next parte ogni volta che viene aggiunto qualcosa allo stream.
al termine dello stream avviene la funzione complete()
![[vlcsnap-2023-01-19-17h36m46s418.png]]

l'utilitá degli streams é che se avviene un errore abbiamo subito a conoscenza dove si trovava un'attimo fa e quindi limitiamo il campo di ricerca dell'errore.