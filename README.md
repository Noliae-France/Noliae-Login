# Noliae Login

Interface Nolc/.nhtml pour `login.noliae.com`, reliée à `/v1/user/login` via
NolCore. Aucun mot de passe ou secret de session n’est manipulé côté client.
La session est un cookie sécurisé, partagé entre les sous-domaines Noliae via
`NOLIAE_COOKIE_DOMAIN=.noliae.com` configuré dans le Core.
