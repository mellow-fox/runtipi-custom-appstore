# Termix

[Termix](https://github.com/LukeGus/Termix) est une application web qui permet d’exécuter des commandes dans un terminal interactif directement depuis le navigateur.  
Elle est pensée comme une alternative simple à des solutions comme **ttyd** ou **wetty**.

---

## Fonctionnalités principales

- Terminal web interactif accessible via un simple navigateur.
- Authentification intégrée pour sécuriser l’accès.
- Personnalisation de la commande de démarrage du shell.
- Léger et rapide (basé sur Node.js et xterm.js).
- Déploiement facile en container Docker.

---

## Utilisation

Une fois installée dans **Runtipi**, l’application est accessible depuis l’URL fournie par la stack.  
Par défaut, Termix expose le port `3000` dans le container.

---

## Variables d’environnement

| Variable         | Description                                                                 | Valeur par défaut |
|------------------|-----------------------------------------------------------------------------|-------------------|
| `TERMIX_USER`    | Nom d’utilisateur pour l’authentification web                               | `admin`           |
| `TERMIX_PASS`    | Mot de passe associé à l’utilisateur                                        | `admin`           |
| `TERMIX_SHELL`   | Shell utilisé dans le terminal (ex: `/bin/bash`, `/bin/zsh`)                | `/bin/bash`       |
| `TERMIX_PORT`    | Port interne de l’application                                               | `3000`            |
| `TERMIX_TITLE`   | Titre affiché dans l’interface web                                          | `Termix`          |

⚠️ **Important** : changez `TERMIX_USER` et `TERMIX_PASS` dès le premier lancement pour sécuriser l’accès.

---

## Exemple de configuration (docker-compose)

```yaml
services:
  termix:
    image: ghcr.io/lukegus/termix:latest
    container_name: termix
    environment:
      - TERMIX_USER=admin
      - TERMIX_PASS=changeme
      - TERMIX_SHELL=/bin/bash
      - TERMIX_PORT=3000
      - TERMIX_TITLE=Termix
    ports:
      - "3000:3000"
    restart: unless-stopped

