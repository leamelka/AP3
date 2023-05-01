# AP3
Cette API permet de réaliser des opérations sur la BDD Mediatek86 qui doit être préalablement créée puis remplie avec le script mediatek86.sql.
L'API actuelle fonctonne avec une BDD MySQL en localhost, port 3306, en accès "root" sans pwd, juste pour des tests en local. Pour une mise en production, il faudra modifier les paramètres du fichier AccessBDD.php et sécuriser la BDD avec un user. Le projet a été fait sous NetBeans.
Pour les tests en local, copier l'API dans le dossier rest_mediatekdocuments (dans le dossier www de wamp ou autre serveur Apache).
Pour accéder à l'API :
localhost/rest_mediatekdocuments/
(suivi des informations données plus bas)
Si l'accès se fait en direct, les login/pwd vont être demandés.
Si l'accès se fait via Postman, il faut préciser le login/pwd dans basic authentication.
Si l'accès se fait par programme, voir la démarche à suivre dans le wiki du dépôt :
https://github.com/CNED-SLAM/MediaTekDocuments
Accès direct au wiki :
https://github.com/CNED-SLAM/rest_mediatekdocuments/wiki/API-s%C3%A9curis%C3%A9e-en-%22basic-authentication%22
Les ajouts suivants dans l'URL permettent de réaliser les opérations suivantes :
Dans les exemples d'url, les informations entre crochets doivent être remplacées par un nom de table ou une valeur d'id (sans mettre les crochets), les informations entre accolades doivent être remplacées par une liste de couples champs/valeur dans les accolades.
En GET :
[table] // contenu de la table (nom donné sans les crochets)
[table]/[id] // contenu d'une ligne d'une table (excepté pour la table 'exemplaire' : liste des exemplaires d'une revue)
En POST :
[table]/{champs} // demande d'ajout dans une table, d'un tuple dont les champs sont passés au format json
En PUT :
[table]/[id]/{champs} // demande d'un tuple (repéré par son id) d'une table, avec les champs à modifier, passés au format json
En DELETE :
[table]/{champs} // demande de suppression dans une table, pour les tuples répondant à tous les critères (et) des champs passées au format json
Résultats obtenus :
Le résultat est au format json, composé de 3 couples :
code : [code]
message : [message]
result : {resultat}
Codes et messages possibles :
200 "OK"
400 "requete invalide"
401 "authentification incorrecte"
500 "erreur serveur"
result contient soit une vide (pour les requêtes autres que GET), soit le résultat du select au format json. 
