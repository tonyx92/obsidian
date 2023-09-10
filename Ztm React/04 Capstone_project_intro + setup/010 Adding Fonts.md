inseriamo nuova font dal sito google fonts https://fonts.google.com/



```html
<link rel="preconnect" href="https://fonts.googleapis.com">  
<link rel="preconnect" href="https://fonts.gstatic.com" crossorigin>  
<link href="https://fonts.googleapis.com/css2?family=Bebas+Neue&display=swap" rel="stylesheet">
```

copio i link in index.html zona head nella cartella public.

nella cartella src vado in index.scss (l'ho modificata da css in scss) e rimuovo i font family non necessare, e inserisco il nome della nuova font che voglio utilizzare.

```scss
body {

  margin: 0;

  font-family: 'Bebas Neue', sans-serif;

  -webkit-font-smoothing: antialiased;

  -moz-osx-font-smoothing: grayscale;

}
```

