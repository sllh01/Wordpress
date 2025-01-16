# Démarrage rapide : Compose et WordPress

Vous pouvez utiliser Docker Compose pour exécuter facilement WordPress dans un environnement isolé
construit avec des conteneurs Docker. Ce guide de démarrage rapide montre comment utiliser
Compose pour configurer et exécuter WordPress. Avant de commencer, assurez-vous d'avoir
[Compose installé](https://docs.docker.com/compose/install/).

## Définir le projet

1. Créez un répertoire de projet vide.

    Vous pouvez donner au répertoire un nom facile à retenir `v1`.
    Ce répertoire est le contexte de l'image de votre application.
    le répertoire ne doit contenir que des ressources pour créer cette image.

    Ce répertoire de projet contient un fichier `docker-compose.yml` qui
    est complet en soi pour un bon projet WordPress de démarrage.

    >**Astuce** : j'ai utilisè une extension `.yml` pour
    ce fichier. Mais on peut aussi utiliser `.yaml` Ils fonctionnent tous les deux.

2. Accédez au répertoire de votre projet.

    Par exemple, si vous avez nommé votre répertoire « my_wordpress » :

    ```console
    $ cd v1/
    ```

3. Créez un fichier `docker-compose.yml` qui démarre votre
    Blog « WordPress » et une instance « MySQL » distincte avec volume
    supports pour la persistance des données :

    ```yaml
    services:
      db:
        # Nous utilisons une image mariadb qui prend en charge les architectures amd64 et arm64
        image: mariadb:10.6.4-focal
        # Si vous voulez vraiment utiliser MySQL, décommentez la ligne suivante
        #image: mysql:8.0.27
        commande : '--default-authentication-plugin=mysql_native_password'
        tomes:
          - db_data:/var/lib/mysql
        redémarrer : toujours
        environnement:
          - MYSQL_ROOT_PASSWORD=unwordpress
          - BASE_DE_DONNÉES_MYSQL=wordpress
          - MYSQL_USER=wordpress
          -MOT DE PASSE MYSQL=wordpress
        exposer:
          - 3306
          - 33060
      WordPress:
        image: wordpress:dernier
        tomes:
          - wp_data:/var/www/html
        ports:
          - 80:80
        redémarrer : toujours
        environnement:
          - WORDPRESS_DB_HOST=base de données
          - WORDPRESS_DB_USER=wordpress
          - WORDPRESS_DB_PASSWORD=wordpress
          - WORDPRESS_DB_NAME=wordpress
    tomes:
      db_data:
      wp_données:
    ```

   > **Remarques**:
   >
   * Les volumes docker `db_data` et `wordpress_data` conservent les mises à jour effectuées par WordPress
   à la base de données, ainsi qu'aux thèmes et plugins installés. [En savoir plus sur les volumes Docker](https://docs.docker.com/storage/volumes/)
   >
   * WordPress Multisite fonctionne uniquement sur les ports « 80 » et « 443 ».
   {: .note-vanilla}

### Construire le projet

Maintenant, exécutez « docker compose up -d » depuis votre répertoire de projet.

Cela exécute [`docker compose up`](https://docs.docker.com/engine/reference/commandline/compose_up/) en mode détaché, extrait
les images Docker nécessaires et démarre les conteneurs WordPress et de base de données, comme indiqué dans
l'exemple ci-dessous.

```console
$ docker compose up -d

Création du réseau « my_wordpress_default » avec le pilote par défaut
Extraction de la base de données (mysql:5.7)...
5.7 : Extraction depuis la bibliothèque/mysql
efd26ecc9548 : Extraction terminée
a3ed95caeb02 : Extraction terminée
<...>
Résumé : sha256:34a0aca88e85f2efa5edff1cea77cf5d3147ad93545dbec99cfe705b03c520de
Statut : Image plus récente téléchargée pour mysql : 5.7
Extraction de WordPress (wordpress:latest)...
dernier: Extraction de la bibliothèque/WordPress
efd26ecc9548 : existe déjà
a3ed95caeb02 : Extraction terminée
589a9d9a7c64 : Extraction terminée
<...>
Résumé : sha256:ed28506ae44d5def89075fd5c01456610cd6c64006addfe5210b8c675881aff6
Statut : Téléchargement d'une image plus récente pour WordPress : latest
Création de ma_base_wordpress_1
Création de mon_wordpress_wordpress_1
```

> **Remarque** : WordPress Multisite fonctionne uniquement sur les ports « 80 » et/ou « 443 ».
Si vous recevez un message d'erreur concernant la liaison de « 0.0.0.0 » au port « 80 » ou « 443 »
(selon celui que vous avez spécifié), il est probable que le port que vous
configuré pour WordPress est déjà utilisé par un autre service.

### Lancez WordPress dans un navigateur Web

À ce stade, WordPress devrait fonctionner sur le port « 80 » de votre hôte Docker,
et vous pouvez terminer la « célèbre installation en cinq minutes » en tant que WordPress
administrateur.

> **Remarque** : le site WordPress n'est pas immédiatement disponible sur le port « 80 »
car les conteneurs sont encore en cours d'initialisation et peuvent prendre quelques
minutes avant le premier chargement.

Si vous utilisez Docker Desktop pour Mac ou Docker Desktop pour Windows, vous pouvez utiliser
`http://localhost` comme adresse IP et ouvrez `http://localhost:80` dans un navigateur Web
navigateur.

![Choisissez la langue pour l'installation de WordPress](doc/1.png)

![WordPress Bienvenue](doc/2.png)

### Arrêt et nettoyage

La commande [`docker compose down`](https://docs.docker.com/engine/reference/commandline/compose_down/) supprime le
conteneurs et réseau par défaut, mais préserve votre base de données WordPress.

La commande `docker compose down --volumes` supprime les conteneurs par défaut
réseau et la base de données WordPress.
