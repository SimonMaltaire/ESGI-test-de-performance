# Plan test de performance de Foodify

### 28/06/2022
### 4IW2
### MALTAIRE Simon
### POLLET Antoine
### LIN Antoine

# Plan test de performance Projet annuel

## 2) Préambule

Description du projet :

La description doit contenir (liste non exhaustive) :

Description globale du projet :
TripAdvisor est un site web américain qui offre des avis et des conseils touristiques émanant de consommateurs sur des hôtels, restaurants, villes et régions, lieux de loisirs, etc., à l'international.
Propose un comparateur de prix pour les vols, réservation d'hôtel etc...
Propose des activités personnalisés.

Objectif de l'application :
Fournir des avis et des conseils venant de consommateurs des services proposés par différents établissement.
Facilité l'accès à différents informations autour du tourismes et voyages

Type d'utilisateurs prévus :
Prévus pour des utilisateurs qui donne et cherche des avis sur différents type d'établissement.
Des établissements qui veulent se mettre en avant.
Des entreprises qui proposent des services touristiques.

Toute autre information que vous jugez pertinente :

## 3) Architecture de l'application
React / MooTools
Fastly
Amazon Ads
Google tag

## 4. Exigences du test

|     Business Transactions     | User Load | Response Time | Transactions per hour |
|:-----------------------------:|:---------:|:-------------:|:---------------------:|
|        Page d'accueil         |  700 000  |  150 - 400ms  |        850 000        |
| Chercher un produit / service |  450 000  |  100 - 255ms  |        750 000        |
| Resever le produit / service  |  250 000  |  150 - 350ms  |        550 000        |
|             Login             |  220 000  |  100 - 300ms  |        250 000        |
|     Effectuer un paiement     |  170 000  |  100 - 300ms  |        170 000        |

## 5. Environnement de test
Précisez l'environnement dans lequel vont se dérouler les tests :
- AMD Ryzen 5 5600G Wraith Stealth (3.9 GHz / 4.4 GHz) , 16 Go Ram * 2
- Linux

Comparez à l'environnement de production, et si possible calculer le coefficient proportionnel : si vous avez 2 CPU en prod, 1 seul pour les tests, alors vous aurez un coefficient de 0.5 (100 utilisateurs en prod reviennent à 50 utilisateurs pour l'environnement de test).

## 6. Planification des tests
L'objectif ici est de déterminer les besoins performatifs de votre application en production, de déterminer les métriques que vous souhaitez surveiller et les critères de réussite de votre test.

Pour cela, vous devrez :
1. Les microservices ont beaucoup de qualités mais aussi quelques défauts : de moins bonne performance,
   Plus difficile à maintenir le réseau (a moins de tolérance aux pannes, a besoin de plus d'équilibrage de charge, etc.)
2. 
3. Load testing - Spike testing - Volume testing
4. Mémoire utilisé, nombre de session active, temps de réponse pour l'affichage d'un produit
5. Moins d'1% au vu du parcours utilisateur.

Consignez ces informations.

## 7. Etapes des tests
Détaillez les étapes des actions utilisateurs pour chaque process. Pour chaque script ainsi créé, un script de test de performance devra être réalisé.

Exemple :

| Step # |     Business Process Name     |
|--------|:-----------------------------:|
| 1      |           Home Page           |
| 2      |      Afficher les offres      |
| 3      | Chercher un produit / service |
| 4      | Resever le produit / service  |
| 5      |             Login             |
| 6      |     Effectuer un paiement     |

En fonction des process choisis, établissez les jeux de données nécessaires. Prodiguez les détails sur le type de données, leur quantité et leur provenance (clone de la prod, fichiers csv créés uniquement pour ce test par exemple).

Données relatives à l'utilisateur, les topics créés, favoris, messages etc ...

Séparez les jeux de données internes aux process (clés API, credentials, ...) et ceux externes (remplissage de la base de donnée).

Credentials → Bearer Token → Envoie du token à chaque requête