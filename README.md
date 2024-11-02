# KMC x CK - Map Application

Cette application web permet d'afficher une carte satellite interactive avec la possibilité de dessiner un polygone et de calculer la surface sélectionnée. Elle utilise l'API HERE Maps pour afficher la carte et proposer des suggestions d'adresses, ainsi que Turf.js pour le calcul de la surface du polygone.

## Fonctionnalités

- **Recherche d'adresse** : Entrez une adresse pour centrer la carte à cet emplacement.
- **Dessin de polygone** : Cliquez sur "Dessiner une surface" pour activer le mode de dessin. Cliquez sur la carte pour ajouter des points au polygone.
- **Calcul de surface** : Une fois le polygone fermé, la surface est calculée et affichée en m².
- **Effacer** : Cliquez sur "Effacer" pour supprimer le polygone et les marqueurs et réinitialiser la carte.

## Prérequis

1. **API Key HERE Maps** : Pour utiliser cette application, vous avez besoin d'une clé API HERE Maps. Vous pouvez l'obtenir en vous inscrivant sur <a href="https://developer.here.com/" target="_blank">HERE Developer</a>.
2. **Connexion Internet** : La carte et les services de recherche nécessitent une connexion Internet.

## Installation

1. Clonez ce dépôt ou copiez les fichiers dans votre répertoire local.

   ```bash
   gh clone clement-krv/KMC---Carte-interactive
   cd KMC---Carte-interactive
    ```
2. Ouvrez le fichier index.html dans votre éditeur préféré.

3. Remplacez la clé API : 
Dans le code, assurez-vous que la clé API HERE Maps est correcte : 

    ```javascript
    const platform = new H.service.Platform({
    apikey: 'VOTRE_CLE_API_HERE'
    });
    ```

Pour pouvoir avoir sa propre clé API veuillez suivre cette documentation <a href="https://www.here.com/docs/bundle/maps-api-for-javascript-developer-guide/page/topics/quick-start.html" target="_blank">ici</a>

4. Lancez le fichier index.html dans votre navigateur pour voir l'application.

## Utilisation

1. Recherche d'adresse : 

- Entrez une adresse dans la barre de recherche sous la carte.
- Sélectionnez l'adresse parmi les suggestions pour centrer la carte à cet endroit.

2. Dessin de polygone :

- Cliquez sur le bouton "Dessiner une surface".
- Cliquez sur la carte pour ajouter les sommets du polygone.
- Cliquez sur le premier point pour fermer le polygone.

3. Calcul de surface :

- Une fois le polygone fermé, la surface est automatiquement calculée et affichée sous la carte.

4. Effacer :

- Cliquez sur "Effacer" pour supprimer le polygone et tous les points associés.

## Structure du projet

- **index.html** : Contient le code HTML et JavaScript pour l'application.
- **Dépendances** :

    - Tailwind CSS : Utilisé pour le style.
    - HERE Maps SDK : Fournit la carte et les services d'interaction.
    - Turf.js : Utilisé pour calculer la surface du polygone dessiné.

## Détails techniques 

### Principales bibliothèques et APIs

- HERE Maps SDK : Fournit la carte satellite, le contrôle de zoom et les interactions de clic. Permet également la recherche d'adresses via l'API Autosuggest.
- Turf.js : Utilisé pour calculer la surface du polygone en m².

### Logique de dessin

- Lorsque "Dessiner une surface" est activé, le mode de dessin est activé, et chaque clic sur la carte ajoute un point au polygone.
- La surface est calculée une fois que le polygone est fermé en cliquant sur le premier point.
- L'application utilise des marqueurs pour les points du polygone et des lignes pour visualiser les segments du polygone en cours de création.

### Personnalisation

Vous pouvez ajuster certains styles et comportements dans le code :

- Style du polygone et des marqueurs : La couleur, la taille, et la transparence des lignes et des points peuvent être modifiées directement dans le code.
- Tolérance pour fermer le polygone : La variable tolerance (en pixels) détermine la distance requise pour détecter le premier point lors de la fermeture du polygone.

## Dépannage 

- Problème de chargement de carte : Assurez-vous que votre clé API HERE Maps est valide et correctement placée dans le code.
- Surface incorrecte : Vérifiez que le polygone est bien fermé avant de calculer la surface. Turf.js nécessite un polygone correctement formé.

## Exemple de code

Voici un extrait montrant l'initialisation de la carte et l'ajout de la fonctionnalité de dessin :

```javascript
const platform = new H.service.Platform({
  apikey: 'VOTRE_CLE_API_HERE'
});
const map = new H.Map(document.getElementById('mapContainer'), platform.createDefaultLayers().raster.satellite.xbase, {
  center: { lat: 48.8566, lng: 2.3522 },
  zoom: 12,
});
```

## Auteur 

Développé par <a href="https://www.linkedin.com/in/votre_nom_utilisateur" target="_blank">Clément Kerviche</a> en partenariat avec <a href="https://komunic.com" target="_blank">Komunic</a>