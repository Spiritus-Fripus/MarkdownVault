# Cours sur les Failles CSRF en PHP

## Introduction

Les attaques CSRF (Cross-Site Request Forgery) représentent une menace majeure pour les applications web. Ces attaques exploitent la confiance accordée par un site à l'utilisateur en lui faisant exécuter des actions non désirées à son insu. PHP, étant l'un des langages de programmation les plus utilisés pour le développement web, est souvent la cible de telles attaques. Ce cours vise à expliquer en quoi consistent les failles CSRF et comment les éviter lors du développement d'applications PHP.

## Qu'est-ce que CSRF ?

CSRF est une attaque dans laquelle un attaquant force un utilisateur authentifié à exécuter des actions indésirables sur un site web où cet utilisateur est authentifié. L'attaque exploite le fait que le site web traite les requêtes de l'utilisateur authentifié sans vérifier si la requête est légitime ou non.

## Comment fonctionne une attaque CSRF en PHP ?

1. L'utilisateur authentifié visite un site malveillant tandis qu'il est connecté à un site légitime.
2. Le site malveillant envoie des requêtes HTTP à l'URL d'action du site légitime en utilisant des éléments HTML tels que les balises `<img>`, `<script>`, `<form>`, etc.
3. Ces requêtes sont exécutées par le navigateur de l'utilisateur authentifié, et le site légitime les traite comme des actions légitimes car elles sont accompagnées des cookies d'authentification.

## Comment prévenir les attaques CSRF en PHP ?

Voici quelques bonnes pratiques pour prévenir les attaques CSRF :

1. **Utilisation de jetons CSRF (CSRF tokens) :** Générer et inclure un jeton CSRF unique dans chaque formulaire ou requête HTTP. Ce jeton doit être vérifié côté serveur pour chaque requête afin de s'assurer de son authenticité.

2. **Utilisation de l'en-tête HTTP Referer :** Vérifiez l'en-tête HTTP Referer pour s'assurer que la requête provient de votre propre site. Cependant, cette méthode peut être contournée dans certaines situations.

3. **Utilisation de SameSite Cookie Attribute :** Configurez vos cookies avec l'attribut SameSite pour limiter les risques de CSRF. Avec l'attribut SameSite, les cookies ne seront pas envoyés lors de requêtes provenant d'un autre site.

4. **Validation de l'origine (Origin Header) :** Vérifiez l'en-tête HTTP Origin pour s'assurer que la requête provient bien de votre domaine.

5. **Durée de validité courte des jetons :** Limitez la durée de validité des jetons CSRF pour réduire la fenêtre d'opportunité pour une attaque CSRF.

## Conclusion

Les attaques CSRF peuvent avoir des conséquences graves pour les utilisateurs et les applications web. En comprenant comment ces attaques fonctionnent et en mettant en œuvre des mesures de sécurité appropriées, telles que l'utilisation de jetons CSRF et la validation des en-têtes HTTP, les développeurs PHP peuvent réduire considérablement les risques de ces attaques et assurer la sécurité de leurs applications web.

### Exemple de Faille CSRF en PHP

Supposons que nous ayons une application PHP qui permet à un utilisateur authentifié de changer son mot de passe en soumettant un formulaire.

```php
<!-- Formulaire de changement de mot de passe -->
<form action="change_password.php" method="post">
    <label for="new_password">Nouveau mot de passe :</label>
    <input type="password" id="new_password" name="new_password">
    <button type="submit">Changer le mot de passe</button>
</form>
```

Le fichier `change_password.php` qui traite la demande de changement de mot de passe pourrait ressembler à ceci :

```php
<?php
session_start();

// Vérifier si l'utilisateur est connecté
if (!isset($_SESSION['logged_in']) || $_SESSION['logged_in'] !== true) {
    header('Location: login.php'); // Rediriger vers la page de connexion si non connecté
    exit;
}

// Changer le mot de passe
if ($_SERVER['REQUEST_METHOD'] === 'POST') {
    $new_password = $_POST['new_password'];
    // Code pour changer le mot de passe dans la base de données
    // ...
    echo "Mot de passe changé avec succès !";
}
?>
```

Cette application est vulnérable à une attaque CSRF car elle ne vérifie pas si la demande de changement de mot de passe provient réellement de l'utilisateur authentifié.

### Correction de la Faille CSRF en utilisant des Jetons CSRF

Pour corriger cette faille CSRF, nous pouvons utiliser des jetons CSRF. Voici comment modifier notre formulaire et le script PHP pour inclure et vérifier un jeton CSRF :

#### Formulaire avec Jeton CSRF

```php
<?php
session_start();
$_SESSION['csrf_token'] = bin2hex(random_bytes(32)); // Génération d'un jeton CSRF
?>

<!-- Formulaire de changement de mot de passe avec jeton CSRF -->
<form action="change_password.php" method="post">
    <input type="hidden" name="csrf_token" value="<?php echo $_SESSION['csrf_token']; ?>">
    <label for="new_password">Nouveau mot de passe :</label>
    <input type="password" id="new_password" name="new_password">
    <button type="submit">Changer le mot de passe</button>
</form>
```

#### Script PHP pour le Changement de Mot de Passe avec Vérification du Jeton CSRF

```php
<?php
session_start();

// Vérifier si l'utilisateur est connecté
if (!isset($_SESSION['logged_in']) || $_SESSION['logged_in'] !== true) {
    header('Location: login.php'); // Rediriger vers la page de connexion si non connecté
    exit;
}

// Vérifier le jeton CSRF
if ($_SERVER['REQUEST_METHOD'] === 'POST') {
    if (!isset($_POST['csrf_token']) || $_POST['csrf_token'] !== $_SESSION['csrf_token']) {
        die("Erreur CSRF détectée !");
    }

    // Changer le mot de passe
    $new_password = $_POST['new_password'];
    // Code pour changer le mot de passe dans la base de données
    // ...
    echo "Mot de passe changé avec succès !";
}
?>
```

Avec cette correction, un jeton CSRF est généré à chaque fois qu'un utilisateur charge la page de changement de mot de passe. Ce jeton est ensuite inclus dans le formulaire et vérifié côté serveur lors de la soumission du formulaire. Cela empêche avec succès les attaques CSRF car l'attaquant ne peut pas fournir un jeton CSRF valide sans accès au jeton spécifique généré pour cette session.