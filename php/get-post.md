# GET / POST

## Method

**$\_GET**

GET recupere des valeurs dans l'URL des liens

```php
<?php
# URL(vhost/dossier/page.php?cle1=valeur1&cle2=valeur2id=42&filtre=toto)
echo $_GET["id"];
if (isset($_GET["___"])){

}
?>
```

**$\_POST**

POST recupère des valeurs dans un formulaire

```php
<form action="traitement.php" method="POST" >
    <input type="text" name="clé">
</form>
```

## Faille XSS

**//!! AVANT UN "echo" SYSTEMATIQUEMENT AJOUTER "htlmspecialchars()" !!//**

```php
<?php
if (isset($_POST["form1"]) && $_POST["form1"] == "sent") {
    echo htmlspecialchars($_POST["champ1"]);
    echo "<br/>";
    echo htmlspecialchars($_POST["champ2"]);
}
?>
```

si l'ont entre des balises dans le form le résultat sera une chaine de caractère plutôt que une injection de code

## POO

**objet**

```php
<?php
$objet= new Classe();
echo $objet -> attribut;
$objet -> method();
?>
```

```php
<?php
$objet = new Personnage();
echo $objet -> pointDeVie;
$objet -> attaque()
?>
```

## PDO

```php
$db = new PDO(_____);
// 'new' représente l'instanciation d'une Classe
```

```php
$db = new PDO("mysql:host=localhost;dbname=nom_db;charset=utf8", "username","password");
// !! ATTENTION !! (sensible aux espaces)

```
