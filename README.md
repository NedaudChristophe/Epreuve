Spécialisation Opérationnelle - Sf session 8 - Epreuve
==================================

## Environnement Docker ##

Ce projet nécessite un environnement Docker adapté. Selon votre mode d'installation, et une fois votre container crée, il vous faudra vérifier et corriger si nécessaire chacun des points suivants :
  * module *"rewrite"* activé (par exemple, sous Apache : `a2enmod rewrite && service apache2 reload`)
  * que le module "sqlite3" correspondant à votre version de PHP est bien installé. Par exemple pour une version PHP 7.4 : `apt update && apt install php7.4-sqlite3`
  * si nécessaire, terminez les modifications des configurations (par exemple, en actualisant Apache : `service apache2 reload`)
Le projet se base sur une gestion des données en **SQLite**, et non via MySQL ou MariaDB.


## Lancement du projet ##

Pour les instructions suivantes, nous partirons du principe que vous avez un mappage du port `1234` (*PC hôte*) vers le port `80` de votre container.

Une fois votre environnement Docker lancé, utilisez un terminal pour vous y connecter. Executez `composer self-update` *(mise à jour de Composer, si nécessaire)* et procédez à l'installation des dépendances à la racine du projet (toujours avec Composer). 

Si nécessaire, créez un fichier `.env.local` afin d'y renseigner vos paramètres locaux.

N'oubliez pas d'initialiser la base de données et son contenu. Par exemple, en executant les commandes suivantes : 
  * `php bin/console make:migration` : prépare la migration des données
  * `php bin/console doctrine:migrations:migrate` : rend effectifs les modifications en base de données
  * `php bin/console doctrine:fixtures:load` : injecte les *"fixtures"*, c'est à dire les données par défaut, en base de données

Puis enfin, accédez au projet Symfony par l'intermédiaire de votre navigateur, en saisissant l'URL [http://localhost:1234](http://localhost:1234). 

**Si une erreur SQL est retournée lors de l'ajout ou la modification de données en BDD, il est possible que votre fichier de base SQLite soit en lecture seule...**


## Présentation du projet ##

Le projet proposé pose les bases d'une gestion de blog. Ce projet simpliste gère des **Articles**.

Pour chaque article, une gestion [CRUD](https://fr.wikipedia.org/wiki/CRUD) est déjà implémentée, avec des interfaces déjà mise en place : listing / édition / ajout / suppression de données.

Les **`Articles`** sont définis par les caractéristiques suivantes :
  * `id` : identifiant unique de l'article
  * `titre` : titre de l'article
  * `contenu` : contenu de l'article


## Consignes de réalisation ##

En vous basant sur le code proposé, vous ajouterez une gestion de **Catégories**. 

Cette gestion devra permettre, à partir d'interfaces adaptées :
  * l'ajout de catégories
  * le listing de toutes les catégories
  * la mise à jour des données d'une catégorie
  * la suppression d'une catégorie
  * la liaison d'un article avec une catégorie

Il vous faudra alors modifier les définitions des articles en y ajoutant cette donnée : 
  * `category` : catégorie de l'article -> liaison avec les données **`Category`**

Les **`Category`** seront définies par les caractéristiques suivantes : 
  * `id` : identifiant unique de la catégorie
  * `name` : nom de la catégorie


## Rappels d'URL du projet ##

  * [Page d'accueil](http://localhost:1234) -> redirection vers [http://localhost:1234](http://localhost:1234/article)
  * [Page de listing d'articles](http://localhost:1234/article)
  * Page de détails d'un article dont l'identifiant unique est **1** : [http://localhost:1234/article/1/](http://localhost:1234/article/1/)
  * Page d'édition d'un article dont l'identifiant unique est **1** : [http://localhost:1234/article/1/edit/](http://localhost:1234/article/1/edit/)
  * [Page d'ajout d'un article](http://localhost:1234/article/new/)
  * [Page de listing des catégories](http://localhost:1234/category)
  * Page de détails d'une catégorie dont l'identifiant unique est **1** : [http://localhost:1234/category/1/](http://localhost:1234/category/1/)
  * Page d'édition d'une catégorie dont l'identifiant unique est **1** : [http://localhost:1234/category/1/edit/](http://localhost:1234/category/1/edit/)
  * [Page d'ajout d'une categorie](http://localhost:1234/category/new/)

