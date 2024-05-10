# Les fonctions

**Fonction somme**

```php
function addition($a,$b){
    $result= 0;
    $result = $a + $b;
    return $result ;
} 

echo addition(1,2) // résultat 3

$val1 = 10;
$val2 = 100;
echo addition ($val1,$val2) // résultat 110
```

**Procédure**

```php
function msg($str) {
    echo "Bienvenue ". $str;
}
msg("Maxime"); // résultat : "Bienvenue Maxime"
```
La procédure ne renvoie pas de résultat , c'est la différence principale avec une fonction.

