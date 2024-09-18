
## Dockerize Laravel Project
 - Nginx le serveur pour accéder à l'application
 - Run docker-compose up --build (pour faire builder les images et faire monter les conteneurs)
 - docker exec -it php bash : Pour executer du code php 
 - ls /var/www/html : Pour lister les fichiers mounted dans le conteneur 

### Executer :
```bash
docker-compose up --build
```

#### Si vous n'avez pas trouvez le dossier vendor c'est que l'auto install des dépandances n'a pas été réalisé donc il faut faire :

```bash
docker exec -it php bash

composer install --no-dev --optimize-autoloader
```


* Testez les routes qui accèdent à la base de données
Vous pouvez tester des routes dans votre application Laravel qui interagissent avec la base de données. Par exemple, si vous avez une route qui récupère des enregistrements à partir de la base de données, visitez cette route dans votre navigateur en accédant à 
http://localhost:5000.

* Utilisez Tinker pour tester la connexion
Vous pouvez également utiliser Tinker, l'outil interactif de Laravel, pour tester la connexion à la base de données et exécuter des requêtes directement. Pour ce faire, entrez dans votre conteneur PHP et exécutez :

```bash
docker exec -it php bash
php artisan tinker
```
Puis, dans Tinker, essayez une simple requête :

```bash
DB::table('users')->get();
```



 
 