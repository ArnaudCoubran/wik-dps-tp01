ReadMe.md

# H1 

*Il s'agit d'une implémentation de base d'un simple serveur HTTP dans Rust. Le serveur écoute 127.0.0.1:8080les connexions TCP entrantes et répond aux requêtes HTTP GET. Les routes prises en charge sont "/ping" et toute autre route, renvoyant respectivement un statut "200 OK" ou "404 NOT FOUND".*


*Pour exécuter le serveur, assurez-vous que Rust est installé, puis exécutez :
cargo run 127.0.0.1.8080*

Le serveur commencera à écouter sur 127.0.0.1:8080.


Le code utilise les bibliothèques Rust standard, notamment :

std::fspour les opérations du système de fichiers.
std::iopour les opérations d’entrée/sortie.
std::netpour les composants de réseau.


Comment ça fonctionne


Le serveur se lie à l'adresse 127.0.0.1:8080 à l'aide d'un écouteur TCP.
Pour chaque connexion entrante, il génère un nouveau thread pour gérer la connexion.
La handle_connectionfonction traite le flux TCP entrant.
Il lit la ligne de requête du client à l'aide d'un fichier BufReader.
En fonction de la demande, il définit la ligne d'état HTTP appropriée et sélectionne le fichier à servir.
Le contenu du fichier sélectionné est lu et sa longueur est calculée.
Le serveur construit une réponse HTTP avec la ligne d'état, la longueur du contenu et le contenu du fichier.
La réponse est renvoyée au client via le flux TCP.


curl -X GET http://127.0.0.1:8080/ping: Renvoie le statut "200 OK" avec le contenu de "bonjour.html".
  
Tout autre itinéraire : renvoie le statut "404 NOT FOUND" avec le contenu de "404.html".