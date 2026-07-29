<div align="center">

# Noliae Login

### Connexion sécurisée Noliae — Nolc MVC

[![CI](https://github.com/Noliae-France/Noliae-Login/actions/workflows/ci.yml/badge.svg)](https://github.com/Noliae-France/Noliae-Login/actions/workflows/ci.yml)

</div>

Application de connexion pour **`login.noliae.com`**, rendue côté serveur avec
Nolc/.nhtml et alignée sur la charte graphique Noliae.

## Flux de sécurité

```text
login.noliae.com → reverse proxy → NolCore /v1/user/login
                                      └→ Set-Cookie nol_session
```

Le navigateur reçoit uniquement le cookie émis par NolCore. Le frontend ne peut
ni lire ce cookie (`HttpOnly`), ni fabriquer une session, ni connaître le secret
HMAC. En production, partagez la session entre les sous-domaines uniquement via
`NOLIAE_COOKIE_DOMAIN=.noliae.com` avec HTTPS et `Secure=true`.

## Exploitation

```sh
nolc nhtml views/login.nhtml
nolc check main.nol
docker build -t noliae-login .
```

La CI construit l’image native, vérifie la santé et publie
`ghcr.io/noliae-france/noliae-login:main`.
