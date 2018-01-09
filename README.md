# comanche

Serveur HTTP en Perl au nom un poil inspiré d'Apache.

## Notes de développement

* Les projections dynamiques sont supportées, mais elles ne prennent pas en charge les variables d'environnement nécessaires pour CGI ;
* L'erreur `418 I'm a teapot` est renvoyée lors d'une tentative de préparation de café à l'aide de l'[HyperText Coffee Pot Control Protocol](https://tools.ietf.org/html/rfc2324).

## Mise en route

Comanche nécessite deux modules Perl installables via le CPAN :

* `Switch`, utilisé pour le traitement de la ligne de commande ;
* `File::MimeInfo`, pour l'identification des types MIME de fichiers.

Pour installer ces modules via le CPAN :

```
$ cpan
cpan> install Switch
cpan> install File::MimeInfo
cpan> exit
```

## Répartition des tâches

* Lucidiot
  * Gestion des processus et signaux
  * Commande de démarrage, d'arrêt, de statut
  * Répartisseur de requêtes
  * Envoi de headers HTTP
  * Gestion des projections statiques
  * Envoi des logs au superviseur
* Pierant
  * Superviseur
  * Chargement de la configuration
  * Chargement des routes
  * Envoi d'erreur HTTP
  * Affichage du contenu d'un répertoire
  * Gestion des projections dynamiques
