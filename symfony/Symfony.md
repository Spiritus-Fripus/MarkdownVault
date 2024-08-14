## Liens utiles

- https://packagist.org/ -> Librairie PHP 
- https://symfony.com/doc/current/index.html -> doc symfony
## Mise en route 

```shell
symfony new nomduprojet --webapp  --version"lts"
# Création du projet avec la version lts
```

## Commandes utiles
```shell
symfony serve # lance le server symfony
symfony server:stop # stop le server
symfony console # liste des commande
symfony console make:controller # crée un controller
symfony console asset-map:compile # compile les asset pour plus de rapidité
symfony console doctrine:database:create  # crée la base de donnée
symfony console make:entity # crée une table
symfony console make:migration # migre la table sur la db
symfony console doctrine:migration:migrate # (d:m:m) 
```

## Import de bootstrap

**_import bootstrap css_**
```shell
php bin/console importmap:require bootstrap/dist/css/bootstrap.min.css
```
**_import bootstrap js_** 
```shell
php bin/console importmap:require bootstrap/dist/js/bootstrap.min.js
```
**_asset/app.js -> Ajouter les lignes_**
```js
import "bootstrap/dist/css/bootstrap.min.css"
import "bootstrap/dist/js/bootstrap.min.js"
```
## Definition

**ORM** -> Object Relational Mapper 
(Utiliser l'objet pour communiquer avec la base de donnée)

_Exemple d'ORM PHP : 
- **Doctrine** 

## Doctrine 

Entity : POST -> Repository : PostRepository
Post => Schema
PostRepository => Actions (C**R**UD) 

Par défaut un Repository se crée avec 4 méthode :
```php
findAll(); // Permet de récuperer tout
find($id); // Permet de récuperer un element par sa clé primaire
findOneBy(); // Permet de récuperer un element par critères
findBy(); // Permet de récuperer tout les élément du critère
```

## Ajout de clés étrangères

Selection de l'entité existante 

Exemple : 
```shell
symfony console make:entity Post # Selection de l'entité existante
```

Suivre les étapes :

- Nommer la clé étrangère pour son type : relation
Exemple :
- La relation entre Post et Tag étant de 0,N -> 0,N : ManyToMany

Pour finir : 
```shell
symfony console make:migration
symfony console doctrine:migration:migrate
```

## DQL (Doctrine Query Langage)

Exemple de liaison d'une table en DQL :

```php
public function findAllWithTags()  
{  
    return $this->createQueryBuilder('p')  
        ->select('p, t')  
        ->join('p.tags','t')  
        ->getQuery()  
        ->getResult();  
}
```

## CRUD

Création d'un crud 

```shell
symfony console make:crud
```

**_Exemple_** :

Suivre les instructions : 
- Choix de l'entité pour le crud
```shell
The class name of the entity to create CRUD (e.g. DeliciousGnome):
> Post
```
- Choix du nom du controller
```shell
Choose a name for your controller class (e.g. PostController) [PostController]:
 > PostCrudController
```
- Accés au crud -> 127.0.0.1:8001/post/crud/

## Formbuilder

Exemple de création d'un formulaire avec FormBuilder :

```php
class PostType extends AbstractType  
{  
    public function buildForm(FormBuilderInterface $builder, array $options): void  
    {  
        $builder  
            ->add('title')  
            ->add('content')  
            ->add('createdAt', null, [  
                'widget' => 'single_text',  
            ])  
            ->add('tags', EntityType::class, [  
                'class' => Tag::class,  
                'choice_label' => 'label',  
                'multiple' => true,  
                'expanded' => true,  
            ])  
        ;  
    }  
  
    public function configureOptions(OptionsResolver $resolver): void  
    {  
        $resolver->setDefaults([  
            'data_class' => Post::class,  
        ]);  
    }  
}
```
