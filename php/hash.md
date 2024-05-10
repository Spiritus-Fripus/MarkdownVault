# Password hash principe

En PHP, un mot de passe est généralement hashé avant d'être stocké dans une base de données pour des raisons de sécurité. Hasher un mot de passe signifie le transformer en une chaîne de caractères aléatoire et unique à l'aide d'un algorithme de hashage. Cela rend le mot de passe illisible et difficile à inverser, ce qui le rend plus sécurisé en cas de compromission de la base de données.

Voici un exemple de hashage de mot de passe en PHP à l'aide de la fonction `password_hash()` :

```php
<?php

$password = "motdepasse123";

// Hasher le mot de passe
$hash = password_hash($password, PASSWORD_DEFAULT);

// Stocker le hash dans la base de données
// Par exemple, en utilisant PDO pour se connecter à la base de données
// (c'est juste un exemple, assurez-vous de configurer correctement votre connexion à la base de données)
$db = new PDO('mysql:host=hostname;dbname=dbname', 'username', 'password');
$stmt = $db->prepare("INSERT INTO users (username, password_hash) VALUES (:username, :password_hash)");
$stmt->bindParam(':username', $username);
$stmt->bindParam(':password_hash', $hash);
$username = "utilisateur";
$stmt->execute();
```

- La fonction `password_hash()` prend le mot de passe à hasher en premier argument et l'algorithme de hashage à utiliser en deuxième argument. PASSWORD_DEFAULT utilisera l'algorithme recommandé par PHP, mais vous pouvez également spécifier un algorithme spécifique si nécessaire.

- Le hash généré est ensuite stocké dans la base de données, généralement avec le nom d'utilisateur associé.

Il est également important de noter que pour vérifier un mot de passe hashé, vous utiliserez la fonction `password_verify()` en PHP. Voici un exemple :

```php
<?php

$login_password = "motdepasse123";
$stored_hash = ""; // Récupérer le hash stocké depuis la base de données

// Vérifier si le mot de passe correspond au hash stocké
if (password_verify($login_password, $stored_hash)) {
    // Le mot de passe est correct
    echo "Mot de passe correct !";
} else {
    // Le mot de passe est incorrect
    echo "Mot de passe incorrect !";
}
```

Cela vérifiera si le mot de passe fourni lors de la tentative de connexion correspond au hash stocké dans la base de données. Si la correspondance est trouvée, cela signifie que le mot de passe est correct. Sinon, le mot de passe est incorrect.
