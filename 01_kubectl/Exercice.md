# Exercice : le CLI "kubectl" 

Dans cet exercice nous allons introduire et manipuler les composants de bases de Kubernetes avec le **CLI "kubectl"**.
Ces composants seront décrits en détails dans la suite de la formation. 

__Les - Vos - Applications sont au coeur de Kubernetes__.

Chaque fonction de l'application (Frontend, Backend... ) peut avantageusement utiliser la containeurisation - avec Docker par exemple. 

C'est là que le système Kubernetes rentre en scène. Son rôle: piloter harmonieusement l'ensemble des containers formant l'application. 
Pour maintenir le cap tout au long du cycle de vie de l'application, Kubernetes utilise des composants : Pods, ReplicatSet, Deployments... 
Ces composants permettent le pilotage programmatique et donc la fourniture des capacités d'automatisation et d'orchestration tout au long du cycle de vie de l'application. Ceci en parfaite correspondance avec les bonnes pratiques DevOps. 

Cet exercice se focalise sur le set de commandes *kubectl* et nous soumettrons directement via le CLI les options a passer au système K8s. 
Plus tard nous envisagerons le provisionning d'Applications, qui consiste à automatiser le déploiement des Pods et des objects nécessaires à leur orchestration, au travers de fichiers de configurations .yaml . 


## Objectifs 

A la fin de l'exercice nous aurons déployé __en ligne de commande via *kubectl*__ une application Hello-Node telle que :

![Architecture Cible de l'exercice](https://github.com/Treeptik/training-k8s-by-treeptik/blob/laurent-branch/tmp_exos/01_kubectl/images/Treeptik-training-k8s-exo1.jpg?raw=true "Architecture Cible de l'exercice")

La charge de travail déployée via un POD est conteneurisé en utilisant Docker. Kubernetes via l'objet ReplicaSet sera en mesure de provisionner plusieurs replicas. L'image du container est disponible sur :

`/chemin/du/repository `
A définir. 

Sources : 

`https://github.com/Treeptik/training-k8s-by-treeptik/tree/laurent-branch/tmp_exos/01_kubectl/sources`


## 1 - Cluster, Pod, Deployment sur Kubernetes 

Se connecter au Cluster K8s de votre environnement de lab provisionné précedemment. 

- En vous aidant de la completion venant avec CLI "kubectl" et de la documentation de *kubetcl* :
1. Lister toutes les options disponibles avec la commande kubectl. 
2. Lister tous les objets disponibles en option de `kubectl get`
3. Quel est le résultat de la commande ? Commentez : 
 
`kubectl get pods `

4. Utiliser *kubectl* pour *lancer* un POD avec les options : 
* nom du POD : hello-world 
* image : hub.docker/.../hello-node:v1 ( à déterminer)
* port : 8080

La sortie de la commande devrait afficher : 

`deployment "hello-node" created `

Kubernetes a crée automatiquement un "Deployment". Cet objet, qui sera etudié plus tard, est utilisé pour orchestrer le POD hello-world tout au long de son cycle de vie : create, scale... .

5. Quel est le résultat de la commande :  
 
`kubectl get pods `

Etudions les informations données par la sortie de ces commandes - en particulier : 

6. Identifier la Colonne "NAME", à votre avis que représente la première ligne *hello-node-.....* ?
7. Identifier la Colonne "READY", à votre avis à quoi correspondent les chiffres : "1/1" ? 

- Le Status du POD est normalement en mode '"Running". En vous aidant de la documentation (trouvée sur Internet)
8. Trouver la liste de tous les *status* possible dans le cycle de vie d'un POD. 
9. Trouver la commande qui affiche les logs temps reels du pod "hello-node"
10. Est-il possible de voir les logs du conteneur executé dans le pod "hello-node" - comment ? Trouver la commande. 


## 2 - Scalabilité - en mode déclaratif - sur Kubernetes.  

Le provisionning à la demande est une fonctionnalité clef de K8s. Il est facile de scaler son application - et de fournir la capacité juste nécessaire - pour répondre aux requêtes utilisateurs en fontion des pics de charge. 

__L'approche de K8s est déclarative__ : il s'agit de "déclarer" le nombre d'instance / de replica que l'on souhaite avoir en tout temps. 

L'objet ReplicatSet qui sera etudié en détail dans la suite de la formation sert à maintenir le nombre de replica au niveau souhaité. 

11. Scaler le replicaset : de 1 à 5 replicas 

- Obtenir la description du nouveau Deployment en tapant la commande : 

`kubectl get deployment ` 

12. Quelle est la signification de chaque colonnes "DESIRED", "CURRENT", "UP-TO-DATE", "AVAILABLE"
13. Obtenir la liste de toutes les instances du POD.  




