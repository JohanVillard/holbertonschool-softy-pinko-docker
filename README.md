# holbertonschool-softy-pinko-docker

## Déploiement de l'application avec Docker

### Prérequis

Avant de déployer l'application, assurez-vous d'avoir les éléments suivants installés :

- **Docker** : Assurez-vous d'avoir Docker installé sur votre machine. Vous pouvez télécharger Docker depuis [le site officiel](https://www.docker.com/get-started).
  
- **Docker Compose** : Docker Compose est un outil pour définir et exécuter des applications multi-conteneurs. Vous pouvez l'installer depuis [la page de documentation officielle](https://docs.docker.com/compose/install/).

### Étapes de Déploiement

1. **Clonez le dépôt**  
   Clonez le dépôt Git contenant l'application :

   ```bash
   git clone https://github.com/JohanVillard/holbertonschool-softy-pinko-docker.git 
   cd task6

2. **Construire et démarrer les conteneurs**
   Utilisez Docker Compose pour construire et démarrer tous les services définis dans le fichier docker-compose.yml :

    ```bash
    docker-compose up --build
    ```

   Cette commande va :

    - Construire les images Docker pour le front-end, le back-end et le reverse proxy à partir de leurs Dockerfiles respectifs.
    - Démarrer tous les services définis dans le fichier docker-compose.yml, incluant le front-end, le back-end et le proxy Nginx.
    - Régler automatiquement les dépendances entre les services (grâce à la directive depends_on), garantissant que le front-end et le back-end démarrent avant le reverse proxy.

3. **Accéder à l'application**

   Une fois les conteneurs lancés, vous pouvez accéder à l'application via les ports définis dans le fichier docker-compose.yml :

    - Front-end : Accédez à l'interface utilisateur via http://localhost:9000.
    - Back-end : L'API est accessible via http://localhost:5252.
    - Reverse Proxy (Nginx) : Si vous avez configuré Nginx pour gérer les requêtes entre le front-end et le back-end, vous pouvez y accéder via http://localhost.

4. **Vérifier l'état des services**

   Vous pouvez vérifier l'état des conteneurs avec la commande suivante :

    ```bash
    docker-compose ps
    ```

   Cela vous donnera un aperçu de l'état des services (front-end, back-end, proxy) et des ports associés.

5. **Arrêter l'application**

   Pour arrêter tous les conteneurs en cours d'exécution, vous pouvez utiliser la commande :
    ```bash    
    docker-compose down
    ```

   Cela arrêtera les conteneurs et supprimera les réseaux et volumes associés à l'application.

### Variables d'Environnement

 - FLASK_RUN_HOST : Définit l'hôte sur lequel Flask doit écouter (par défaut 0.0.0.0).
 - FLASK_RUN_PORT : Définit le port sur lequel Flask doit écouter (par défaut 5252).

Ces variables sont définies dans la section environment du service back-end dans le fichier docker-compose.yml.

### Personnalisation des ports

 - Le front-end est exposé sur le port 9000 pour l'interface utilisateur.
 - Le back-end est exposé sur le port 5252 pour l'API.
 - Le reverse proxy Nginx est configuré pour écouter sur le port 80.

Vous pouvez ajuster ces ports dans le fichier docker-compose.yml si nécessaire.

### Dépannage

 - Si les conteneurs ne démarrent pas, vérifiez les logs pour chaque service avec la commande :

   ```bash
   docker-compose logs <nom_du_service>
   ```

   Par exemple, pour les logs du front-end :


   ```bash
   docker-compose logs front-end
   ```
