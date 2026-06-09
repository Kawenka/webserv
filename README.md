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
