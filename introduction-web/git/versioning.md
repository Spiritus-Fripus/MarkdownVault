# Versioning

## Definition

Le versioning fait référence à la gestion des différentes versions d'un logiciel, d'un fichier, ou d'un projet. Il s'agit d'un processus qui permet de suivre les modifications apportées au fil du temps, d'organiser les différentes versions, et de faciliter la collaboration entre plusieurs personnes travaillant sur le même projet. Le versioning est largement utilisé dans le développement de logiciels, la gestion de projets, et même dans le domaine du contenu multimédia.

Il existe différents systèmes de versioning, notamment le versioning centralisé et le versioning décentralisé. Parmi les outils de versioning les plus couramment utilisés, on trouve Git, Mercurial, Subversion, et d'autres.

L'utilisation d'un système de versioning permet de garder une trace des modifications apportées, de revenir à des versions antérieures si nécessaire, de gérer les conflits entre les modifications concurrentes, et de faciliter la collaboration en permettant à plusieurs personnes de travailler simultanément sur un même projet sans risque de pertes de données.

![versioning](https://d36ai2hkxl16us.cloudfront.net/course-uploads/3eb5fe9d-f865-4dce-9bb3-54c11277cbaf/m4tnzu0vk1hf-semantic-versioning.jpg)

**`Exemple :`**

```mermaid
graph TD;
ESN --> clientX
ESN --> clientY
ESN --> clientZ
clientX -->|V1.0| serveur
clientY -->|V2.0| serveur
clientZ --> APP
APP -->|V2.1| serveur
```
