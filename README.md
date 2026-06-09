```text
webserv/
├── Makefile
├── inc/
│   ├── config/       # .hpp pour le parsing du fichier .conf
│   ├── core/         # .hpp globaux (structures communes, utils)
│   ├── http/         # .hpp pour les requêtes/réponses HTTP
│   └── network/      # .hpp pour le serveur, les Sockets, poll()
├── srcs/
│   ├── main.cpp
│   ├── config/       # .cpp pour le fichier .conf
│   ├── cgi/          # .cpp pour le CGI
│   ├── http/         # .cpp pour les requêtes
│   └── network/      # .cpp pour le serveur
├── conf/
│   └── default.conf  # fichier de configuration de test
└── www/
    └── index.html    # site web pour faire des tests
```

## 📑 Git Workflow & Branches
| Branche | Description
| :--- | :---:
| `main` | **Version stable du serveur.** Ne jamais coder directement dessus. Doit toujours compiler sans erreur. |
| `feature/config-parser` | Lecture et parsing du fichier `.conf`, validation syntaxique et stockage dans les classes de configuration. |
| `feature/network-core` | Initialisation des sockets, passage en non-bloquant (`fcntl`) et boucle principale du multiplexage (`poll`/`epoll`/`kqueue`). |
| `feature/http-request` | Réception du flux réseau et parsing de la requête HTTP brute (Méthode, URL, Headers, Body, Chunked). |
| `feature/http-response` | Logique de routage, vérification des droits, génération des headers HTTP et envoi des fichiers statiques. |
| `feature/cgi-handler` | Gestion des scripts dynamiques via `fork()`, configuration des variables d'environnement et redirection des flux via `pipe()`. |
| `feature/file-upload` | Gestion des requêtes POST `multipart/form-data` pour permettre aux clients d'uploader et d'enregistrer des fichiers. |
| `feature/autoindex` | Génération automatique d'une page HTML listant le contenu d'un répertoire si le fichier index est absent. |
| `fix/memory-leaks` | Phase de nettoyage avec **Valgrind** : correction des fuites mémoire, gestion rigoureuse des erreurs et des crashs. |
