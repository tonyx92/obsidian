
CRUD (Create, Read, Update, Delete)

![[vlcsnap-2023-01-14-15h56m59s488.png]]


![[vlcsnap-2023-01-14-16h00m27s229 1.png]]


Authentication : 
![[vlcsnap-2023-01-14-16h04m06s434 1.png]]

![[vlcsnap-2023-01-14-16h05m01s410.png]]


Firebase ci permette di utilizzare google sign-in:

1 eseguo una richiesta a google server per verificare l'utente

![[vlcsnap-2023-01-14-16h08m00s052.png]]

2 google Verifica la corrispondenza![[vlcsnap-2023-01-14-16h09m06s252.png]]

3 google genera un auth_token (unique hash string),corrispondente all'utente che vuole registrasi e lo invia al website.![[vlcsnap-2023-01-14-16h09m57s606.png]]

4 website invia auth_token a firebase conferma  per accesso a determinati tipi di dati presenti nel DB, ma questo token non é sufficente, qualcuno potrebbe averlo semplicemente copiato e inviato direttamente a firebase.![[vlcsnap-2023-01-14-16h11m43s317.png]]

5 Firebase ha bisogno di confermare la validitá del token![[vlcsnap-2023-01-14-16h14m14s021.png]]
6 google lo riceve e controlla se é quello che ha inviato e se === true google invia un verification_token![[vlcsnap-2023-01-14-16h15m32s322.png]]
7 Ora che tutto é confermato firebase realizza un access_token che definisce cosa l'user puo accedere all'interno del DB e lo ritorna al website![[vlcsnap-2023-01-14-16h17m02s931.png]]

8 Ora come website con questo token posso effettuare tutte le operazioni CRUD inviandole assieme all'access token verso firebase.![[vlcsnap-2023-01-14-16h18m20s786.png]]

9 firebase controlla sempre la validitá del token, se === true all'ora controlla che le CRUD siano eseguibili![[vlcsnap-2023-01-14-16h19m30s483.png]]
 10 Firebase genera CRUD response e le ritorna se valide![[vlcsnap-2023-01-14-16h20m13s446.png]]
