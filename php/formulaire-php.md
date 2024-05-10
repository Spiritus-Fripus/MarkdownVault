# formulaire 

## $POST
```html
<form method="post" action="_/_/_.php">
    
</form>
```

```php
// $_POST transforme en tableau associatif ["..."=> "______"]
$nom = $_POST['nom'];
if (isset($_POST['nom'])) {
    // isset verifie l'existence du champ['nom']
    $nom = $_POST['nom'];
    foreach ($_POST as $key=>$value){
        // code ici
    }
}
```


