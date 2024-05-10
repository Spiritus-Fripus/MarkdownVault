# Cours sur les attributs async et defer en JavaScript

Les attributs `async` et `defer` sont utilisés dans les balises `<script>` en HTML pour contrôler le chargement et l'exécution des fichiers JavaScript externes. Comprendre la différence entre ces deux attributs est essentiel pour optimiser le chargement des ressources sur une page web.

## 1. `async`

L'attribut `async` spécifie que le téléchargement du fichier JavaScript ne doit pas bloquer le téléchargement des autres ressources de la page. Cela signifie que le script sera téléchargé en parallèle avec d'autres ressources, et l'exécution du script commencera immédiatement après son téléchargement, sans attendre que le reste de la page soit chargé.

```html
<script src="script.js" async></script>
```

Caractéristiques de `async` :

- Le script est téléchargé en parallèle avec d'autres ressources.
- L'exécution du script commence dès que son téléchargement est terminé.
- L'ordre d'exécution n'est pas garanti, ce qui peut être problématique si le script dépend de l'ordre d'exécution.

## 2. `defer`

L'attribut `defer` indique au navigateur de télécharger le fichier JavaScript en arrière-plan pendant que la page HTML est en train d'être analysée. L'exécution du script est différée jusqu'à ce que la structure de la page HTML soit entièrement analysée.

```html
<script src="script.js" defer></script>
```

Caractéristiques de `defer` :

- Le téléchargement du script est différé jusqu'à ce que la page HTML soit entièrement analysée.
- L'ordre d'exécution est préservé, les scripts sont exécutés dans l'ordre de leur apparition dans le code HTML.
- L'exécution du script commence dès que l'analyse du document HTML est terminée, avant l'événement `DOMContentLoaded`.

## 3. Quand utiliser `async` ou `defer` ?

- **Utiliser `async`** lorsque le script ne dépend pas de l'ordre d'exécution et peut être exécuté dès que possible, même si la page n'est pas entièrement chargée. Cela peut être utile pour les scripts de suivi, les widgets intégrés, etc.

- **Utiliser `defer`** lorsque l'ordre d'exécution est important ou lorsque le script manipule le contenu de la page et doit être exécuté après le chargement complet du document HTML.

## Conclusion

Les attributs `async` et `defer` offrent des moyens efficaces de contrôler le chargement et l'exécution des scripts JavaScript externes dans une page web. Comprendre ces attributs et savoir quand les utiliser peut contribuer à améliorer les performances et le comportement global de votre site web.

---

Ce cours devrait fournir une compréhension de base des attributs `async` et `defer` en JavaScript. N'hésitez pas à poser des questions si vous avez besoin de plus de clarifications!
