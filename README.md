# DockerELProject

## Membres :

- Mattéo Christophe
- Romain Ranaivoson

## Résumé

On a fait une media stack téléchargeant automatiquement ou manuellement des films et séries à partir d'interfaces web dédiées.
Ces fichiers sont ensuite disponibles sur le serveur Média Jellyfin.

# Fonctionnalités

### Prowlarr

- Ajout manuel des indexeurs pour avoir des sources de téléchargement
- Ajout automatique des indexeurs **vers** les autres apps

### Sonarr

- Téléchargement manuel de séries et anime
- Téléchargement automatique de séries et anime après ajout dans la bibliothèque
- Calendrier des épisodes à venir
- Ajout automatique dans la bibliothèque Jellyfin

### Radarr

- Téléchargement manuel de films
- Téléchargement automatique de films après ajout dans la bibliothèque
- Gestion des collections de films (trilogies etc...)
- Ajout automatique dans la bibliothèque Jellyfin

### Lidarr

- Téléchargement manuel de musiques
- Téléchargement automatique de musiques après ajout dans la bibliothèque
- Gestion des albums et sorites

### Transmission

Client Torrent permettant de télécharger les fichiers multimédias envoyés par les autres apps

### Jellyfin

- Serveur média rendant disponibles les téléchargements effectués via les autres apps
- Métadonnées des fichiers médias téléchargées automatiquement

### Traefik

- Reverse proxy renvoyant vers les apps pour une facilité d'utilisation, au format **{app}.localhost**
- Tout est paramétré à l'intérieur du fichier Compose, pas de volume nécessaire

# Utilisation

Avant toute chose, entrez dans le dossier où se trouve le fichier Compose., puis effectuez la command `docker-compose up -d`

Si vous voulez télécharger un film :

1. Rendez-vous sur **prowlarr.lcoalhost**
2. Ajoutez un indexeur manuellement (choisissez-en un bon)
3. Paramétrez **Radarr** dans la liste des apps
4. Synchronisez les indexeurs
5. Rendez-vous sur **radarr.localhost**
6. Paramétrez le stockage (`/movies`)
7. Paramétrez le client torrent Transmission (hôte `transmission`)
8. Ajoutez votre film à la bibliothèque et lancez le téléchargement
9. Rendez-vous sur `jellyfin.localhost`
10. Paramétrez la bibliothèque **Films** vers le chemin `/movies`
11. ...
12. Profit !
