# Tableaux

## 1 dimension

**parcourir les index d'un tableau** 

```php
$tab = ['A','B','C'];
echo $tab[1]; // B

$tab[3] = "D"; // ['A','B','C','D'] quand on connait les index

$tab[count($tab)] = "D"; // count permet de connaitre le nombre de tab

$tab[0] = 'AA'; // ['AA','B','C','D'
```
**Affichage des index du tableau**

```php
echo $tab[0];
echo $tab[1];
echo $tab[2];
echo $tab[3];
```

```php
for ($i = 0; $i < count($tab); $i++){
    echo $tab[$i]; 
}
```

## 2 dimensions

```php
echo $tab[2][2]; // affiche un élément précis d'un index voulu

for ($i = 0; $i < count($tab); $i++){
    for ($j = 0; $j < count($tab[$i]); $j++){
        // parcours le tableau et le sous tableau
        echo $tab[$i][$j];
    }
}
```
**Il y aura autant de boucles imbriquées que de dimension dans le tableau pour le parcourir**

```php
$tab = ['A','B','C','D'];

foreach ($tab as $value) { 
    // $value représente les cases du tableau
    echo $value
}
```

## tableaux associatifs

```php
$tab = ['case 1' => 'A', 'case2' => 'B','case3' => 'C'];
// pour afficher l'index [1] on utilise
echo $tab['case2'];

foreach ($tab as $key=>$value){
    // $key représente la clé devant chaques valeurs
    echo $key." ".$value;
}
$tab['case4'] = 'D'; // ajout de 'case4' => 'D'
echo $tab['case5']; // error car aucun case 5
```
