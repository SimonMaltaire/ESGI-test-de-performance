# Redaction d'un Plan pour Reddit (site traffic moyen)

### 28/06/2022, 4IW2
### MALTAIRE Simon, POLLET Antoine, LIN Antoine

## 1. Préambule
### Description
Reddit est un site Web d'actualités sociales et un forum où le contenu est socialement organisé et promu par les membres du site par le biais de votes. Le nom du site est un jeu sur les mots "Je l'ai lu." L'inscription en tant que membre Reddit est gratuite et nécessaire pour utiliser les fonctionnalités de base du site Web.
### Objectif
Apporter des informations à l'utilisateur
### Type d'utilisteur
Utilisateur récurrent passant du temps sur les réseaux sociaux

## 3. Architecture de l'application
Vous allez décrire ici l'architecture de votre application :
- Résumé de l'architecture globale
- React / Nodejs / ELK
- Micro services, PLM, IAM, etc ...

Inclure un diagramme ou schéma décrivant les interactions entre les différentes parties de votre application.

Veuillez renseigner également l'infrastructure de production (heroku, conteneurisation, kubernetes...).

## 4. Exigences du test

| Processus non fonctionnel          |      Infos      |
|------------------------------------|:---------------:|
| User Load                          |   100 million   |
| Temps de répone attendu            | 100 ms - 500 ms |
| Nombre de transactions / par heure | 10 - 20 million |

## 5. Environnement de test
Précisez l'environnement dans lequel vont se dérouler les tests :
- Processeur AMD Ryzen ThreadRipper Pro 3995WX Socket sWRX8 (2,7 Ghz), 32GB RAM
- Linux

Comparez à l'environnement de production, et si possible calculer le coefficient proportionnel : si vous avez 2 CPU en prod, 1 seul pour les tests, alors vous aurez un coefficient de 0.5 (100 utilisateurs en prod reviennent à 50 utilisateurs pour l'environnement de test).

## 6. Planification des tests
L'objectif ici est de déterminer les besoins performatifs de votre application en production, de déterminer les métriques que vous souhaitez surveiller et les critères de réussite de votre test.

Pour cela, vous devrez :
1. Les microservices ont beaucoup de qualités mais aussi quelques défauts : de moins bonne performance,
   Plus difficile à maintenir le réseau (a moins de tolérance aux pannes, a besoin de plus d'équilibrage de charge, etc.) 
2. ?
3. Load testing - Spike testing - Volume testing - Endurance Testing
4. Maximum active sessions - Memory use - Thread counts
5. Less than 2% of failed request

Consignez ces informations.

## 7. Etapes des tests
Détaillez les étapes des actions utilisateurs pour chaque process. Pour chaque script ainsi créé, un script de test de performance devra être réalisé.

Exemple :

| Step # | Business Process Name |
|----|:---------------------:|
| 1  |       Home Page       |
| 2  |         Login         |
| 3  |     Search topic      |
| 4  |      Vote topic       |
| 5  |   Création de topic   |
| 6  |        Logout         |

En fonction des process choisis, établissez les jeux de données nécessaires. Prodiguez les détails sur le type de données, leur quantité et leur provenance (clone de la prod, fichiers csv créés uniquement pour ce test par exemple).

Données relatives à l'utilisateur, les topics créés, favoris, messages etc ...

Séparez les jeux de données internes aux process (clés API, credentials, ...) et ceux externes (remplissage de la base de donnée).

Credentials → Bearer Token → Envoie du token à chaque requête

## 8. Execution des tests
En premier lieu, détaillez le nombre de cycles d'execution de chaque process.
Ajoutez un résumé du scénario de test.

Exemple :

| Test Run        |                 Test Scenario Summary                 |
|-----------------|:-----------------------------------------------------:|
| Smoke Test      | To validate the performance test scripts and monitors |
| Cycle 1 - Run 1 |        Load Test - 1 Hour test with peak load         |
| Cycle 1 - Run 2 |     Repeat Load Test - 1 Hour test with peak load     |
| Cycle 1 - Run 3 |    Spike Test - 30 min test with 150% of peak load    |
| Cycle 1 - Run 4 |                      Volume Test                      |
| Cycle 1 - Run 5 |        Load Test - 1 Hour test with peak load         |
| Cycle 1 - Run 6 |                 Endurance Test - 12 H                 |
| Cycle 2 - Run 1 |        Load Test - 1 Hour test with peak load         |
| Cycle 2 - Run 2 |     Repeat Load Test - 1 Hour test with peak load     |
| Cycle 2 - Run 3 |    Spike Test - 30 min test with 150% of peak load    |
| Cycle 2 - Run 4 |                      Volume Test                      |
| Cycle 2 - Run 5 |        Load Test - 1 Hour test with peak load         |
| Cycle 2 - Run 6 |                 Endurance Test - 12 H                 |

Ensuite, détaillez chaque scénario comme l'exemple suivant (pour le Load Test) :

|  | Test Details |
|--------------|:-----------:|
| **Purpose** | Peak hour transaction processing will be under examination to <br/> determine if the system can maintain response times <br/> under the highest anticipated load. <br/> This test is designed to collect performance <br/> metrics on transaction throughput, response times, <br/> and system resource utilization, <br/> in comparison to Performance requirements. |
| **No. of Tests** | 4 (2 tests per cycle) |
| **Duration** | Ramp-up: X - Steady State: X - Ramp-down: X |
| **Scripts** | 1. XXXX - 2. XXXX |
| **Scenario Name** | Load Test Scenario |
| **User Load / Volume** | 500 Vusers (Threads) Load |
| **Entry Criteria** | 1. The code should be stable and functionally verified <br/> 2. Test Environment should be stable and ready to use <br/> 3. Test Data should be available <br/> 4. All the NFRs should be agreed with the project <br/> 5. Test scripts should be ready to use |
| **Validation Criteria** | 1. The mean of the response time should be below 1.5 sec <br/> 2. The error rate should be below 5% |

## 9. Résultats des tests
Ici, référencez les graphiques et données résultant des tests effectués

## 10. Analyses et Optimisations proposées
Après avoir effectué une comparaison entre les résultats obtenus et ceux escomptés, analyser les résultats et tentez de proposer des axes d'amélioration. Ceux-ci peuvent être :
- Optimisation d'un service grâce a de meilleurs algorithmes
- Optimisation de l'infrastructure (scalabilité accrue par exemple)
- Détection d'éventuels goulots d'étranglements
