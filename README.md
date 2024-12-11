## Partie 1 : Téléchargement et Installation Neoload
Lien de téléchargement :
https://support-hub.tricentis.com/open?id=downloads&version=c65ff071974e6d102066fc70f
053afbb
Outil Neoload:
![image](https://github.com/user-attachments/assets/5459b95b-f6bc-401b-97ed-5413117f6e15)

## Partie 2 : Neoload Overview
Les différentes parties de Neoload : <br>
<b> Design : </b> Cette partie permet d'écrire des scripts, des cas d’utilisations, des conditions logiques, etc <br>
<b>Runtime :</b> Cette partie permet de configurer et de lancer l’exécution des scénarios <br>
<b>Result : </b> Cette partie permet de visualiser, d’analyser et de faire un reporting des résultats <br>
## Partie 3 : Création de projet
## Partie 4 : Design module
Cette partie permet d'écrire des scripts, des cas d’utilisations, des conditions logiques, des corrélations, des paramétrisations, etc.
## Partie 5 : What is workflow
Un workflow est une série d’action effectuée par un utilisateur dans un site ou une
application web. Un workflow est donc l’enregistrement d’un parcours utilisateur. Dans neoload on l’appelle Parcours Utilisateur.
## Partie 6 : Record a workflow
Lorsqu’on enregistre un parcours utilisateur via un navigateur web, on ajoute d’abord le nom de la transaction et ensuite on clique ou bien on navigue vers le lien correspondant au nom
de la transaction donnée.
L’ensemble des noms de transactions vont constituer un workflow.
## Partie 7 : Exploring the user path
A la fin de l’enregistrement de notre workflow, toutes les actions effectuées dans l’application web ou le site sont répertoriées dans le dossier Action, Init, End.
## Partie 8 : User Path hierarchy
Dans un parcours utilisateur, nous avons 3 dossiers : Init, Action, End
● Init et End peuvent être utilisés pour enregistrer les transactions de logIn et de logOut.
● Dans la partie Action, nous avons d’abord le nom de la transaction ensuite la page enregistrée et enfin toutes les ressources de cette page (image, fichier, session, variables, etc)
## Partie 9 : Check User path validity
Après l’enregistrement du parcours utilisateur, il est nécessaire de relancer le parcours dans
neoload pour pouvoir détecter les potentielles erreurs et les variables dynamiques, les
sessions ID, les login, les mots de passes, etc.
<b>La colonne Action  </b>représente le nom de la transaction ou de la requête
<b>La colonne Code de réponse </b> représente le statut de la réponse (200, 404, etc)
<b>La colonne Assertion : ? </b>
<b>La colonne Différence</b>  représente la différence qui existe entre la réponse du serveur lors de l’enregistrement et la réponse du serveur lors de la validation du check user path
## Partie 10 : Google chrome developer Tools
Tous les éléments figurant dans la partie Network de Google Chrome (qui affiche l’ensemble des ressources d’une page web (image, fichiers, css, html, etc) doit se retrouver dans une des transactions enregistrées dans Neoload.
## Partie 11 : Understanding response code
● 100 : informations
● 200 : success
● 300 : redirection
● 400 : client side error
● 500 : server side error
## Partie 12 : Components of request & response
Un request component contient :
● une méthode HTTP (POST, GET, DELETE, PUT, PATCH, etc)
● un URL
● un header (content-type : json, xml, etc)
● un body qui est optionnel
Une réponse component contient :
● un code de réponse ou statut (200, 404, 500, etc)
● un header (content-type : json, xml, etc)
● un body qui est optionnel
Request figure
Response figure
## Partie 13 : Corrélation (extractor variable)
La corrélation est l’action d’identifier, d’extraire et d’utiliser des variables dynamiques provenant du serveur. Aussi, si nous avons des données telles que les CSRF token il est fort probable que lors du lancement du check user path qu’on ait des erreurs car les CSRF
token ne sont joués qu’une seule fois. Le but ici est de pouvoir corriger ces erreurs et faire des tests ressemblant à des cas réels.
Les différents types de corrélation sont :
1. Autocorrelation
2. Automatic configuration
3. Manual correlation
4. Advanced correlation
L'autocorrélation c’est lorsqu’on laisse neoload chercher lui même les variables dynamiques, les extraire et faire la corrélation. Cependant, neoload ne peut pas connaître l’ensemble des variables dynamiques d’un workflow.
Automatic configuration : C’est lorsqu’on laisse neoload dynamiser la variable via la configuration automatique. Ici on passe sur chaque variable dynamique et on applique la configuration automatique.
Manual Corrélation : Il s’agit d’identifier chaque variable dynamique, chercher la variable dans le code source (onglet réponse enregistrée), extraire cette variable dynamique (variable extractor) et enfin la remplacer dans les paramètres des requêtes.
## Partie 14 : Randomization
La randomization est l’action de choisir des variables dynamiques tels que des noms de
catégories ou bien des ID de produits et les lancer dynamiquement via l’extraction de
variable pour se rapprocher beaucoup plus des test réels.
Les différentes étapes de la randomization : identifier les valeurs dynamiques, appliquer
la corrélation sur ces valeurs (via extractor variable) et faire le remplacement dans toutes les
transactions signalées dans le flag request.
Exemple : Lors d’un recording, on ajoute un produit Tapila appartenant à la catégorie fish.
Pour simuler d’autres produits appartenant à Tapila alors on doit implémenter la
randomization.
Important : Dans un site e-commerce, pour simuler des achats de divers produits provenant
de diverses catégories, alors on doit faire une corrélation des catégories, des
sous-catégories (s’il y’en a) et des produits.
Question : Pourquoi lors de la randomization des variables, lorsqu'on fait un flag request
pour déterminer toutes les transactions ayant cette variable là, on commence toujours par la
transaction précédant la transaction sur lequel on a cliqué ?
## Partie 15 : Parametrization (variable)
Les variables sont des données envoyées par le client au serveur. Les variables sont
appelés paramètres dans Neoload.
Ex : Lors d’un login, on envoie le login et le mot de passe au serveur pour une vérification
Nous avons différents types de variables (voir image) : Liste (data in table format), File (txt,
csv), SQL, Integer, String, etc. On peut aussi générer une valeur via le code javascript.
Question : Dans quel cas utiliser les variables SQL (parametrization) ?
## Partie 16 : Flag request
Les flags sont utilisés pour chercher des mots clés, des valeurs, des données dans les
requêtes ou dans les réponses sous certains critères.
## Partie 17 : Assertion
Les assertions permettent de valider une réponse HTTP provenant du serveur sous certains
critères.
Il ya 2 types d’assertions :
● Assertion locale : elle est basée sur le contenu de la réponse HTTP, sa taille et sa
durée
● Assertion globale :
Assertion basée sur la durée : Elle permet de fixer un délai en ms pour le chargement de
telle ou telle page et de voir si cette page parvient à être complètement chargée en fonction
du délai fixé.
Assertion basée sur la taille : L’assertion basée sur la taille permet de faire une
comparaison entre la taille de la réponse HTTP reçue et la taille passée en paramètre. Elle
est utilisée pour ajouter une assertion dans le chargement des fichiers du serveur vers le
client.
Assertion basée sur le contenu de la réponse : Elle permet de vérifier si parmi les
réponse HTTP provenant du serveur nous avons tel ou tel texte ou donnée ou nombre, etc
Assertions globales : on double click sur le nom du parcours utilisateur ou workflow. Cette
assertion va concerner l’ensemble des transactions ou containers.
## Partie 18 : Monitor machine
Les moniteurs dans Neoload nous permettent de visualiser le comportement des serveurs,
des bases de données, de la RAM etc durant l’exécution des tests.
## Partie 19 : Population
Une population est un ensemble d’utilisateurs virtuels ayant des parcours utilisateurs
communs ou différents.
## Partie 20 : Runtime
Runtime permet de mettre en place des scénarios et d'exécuter les tests.
Un workflow est l’ensemble des transactions ou users stories. C’est le parcours utilisateur.
Un scénario permet de définir le type de test de performance que l’on doit exécuter et nous
renseigne sur comment le faire avec ses parties politique de durée, injecteur de charge,
politique de variation de la charge et population (configuré dans la partie population)
Il ya différents types de test de performance :
● Load test
● Smoke test
● Stress test
● Spike test
● Scalability test
● Endurance test
Dans la partie avancé nous avons :
Load variation policy ou politique de variation de la charge : il permet de configurer le
comportement des utilisateurs durant l’exécution des tests. On peut appliquer une charge
constante, une charge croissante, une charge décroissante des utilisateurs.
Duration policy ou politique de durée : il permet de chronométrer la durée du test
Load generator ou injecteur de charge : il permet de partager la charge durant les tests.
## Partie 21 : Smoke Test
Il permet de vérifier si le scripting ne présente aucun problème lors des tests. Ici on ne fait
pas focus sur la charge, on vérifie juste que l’application fonctionne même avec un seul
utilisateur). C’est un test qui dure généralement 15 minutes avec 10 utilisateurs virtuels.
## Partie 22 : Stress Test
Le test de stress s’effectue en envoyant une charge au système au-dessus de la normale
pour voir quels parties du système vont résister ou faiblir face à la montée en puissance des
requêtes.
## Partie 23 : Load Test
Un test de charge est l’action d’envoyer une charge normale à un système et de mesurer les
réponses. Ici on met l’accent sur les temps de réponse dans des conditions de requête
normale.
## Partie 24 : Endurance Test
Le test d’endurance s’effectue en envoyant une charge constante au système pendant
plusieurs heures pour vérifier si le système est capable de tenir le rythme des requêtes
pendant longtemps.
## Partie 24 : Spike Test
Il s’effectue en envoyant des pics de requêtes, d’utilisateurs virtuels par moment dans le
système. La charge peut être croissante comme décroissante.
## Partie 25 : Exécution des Test
Pour exécuter un type de test de performance (test de stress, d’endurance, de charge,
smoke test), il faudrait configurer la partie scénario qui se trouve dans la partie Runtime ou
Exécution.
Ecran scénario
Pour disposer de tous éléments dans la partie scénario, il faudrait au préalable :
Accéder dans la partie Conception qui est divisé en 3 parties : <br>
<b>● Parcours utilisateurs : </b>qui permet de faire le recording ou scripting d’une application web en se basant sur un parcours utilisateur.<br>
<b>● Population :</b> elle permet de configurer tous les types d’utilisateurs virtuels utilisant l’application web. Aussi, des choix concernant les navigateurs et les réseaux (4g, H+, 3g) qu’ils utilisent ainsi que le nombre de chaque type d’utilisateurs virtuels sont configurables. <br>
<b>● Moniteurs et connecteurs : </b> elle permet d’ajouter des équipements (serveur, machine, OS), des bases de données, des RAM etc sur laquelle vont s’exécuter nostypes de test.
