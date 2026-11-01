# jeux

Index page of my online multiplayer games, served at [jeux.jdelgado.fr](https://jeux.jdelgado.fr).

| Game | URL |
| --- | --- |
| UNO | [uno.jdelgado.fr](https://uno.jdelgado.fr) |
| Belote | [belote.jdelgado.fr](https://belote.jdelgado.fr) |
| Jeu de l'oie | [oie.jdelgado.fr](https://oie.jdelgado.fr) |

## Add a game

1. Put its icon in `public/icons/<game>.svg`.
2. Copy a `<li>` in `public/index.html` and change the link, the icon and the text.

## Run locally

```bash
docker build -t jeux .
docker run --rm -p 8088:8080 jeux   # http://localhost:8088
```

## Deploy

Behind an existing Traefik: replace `REPLACE_RESOLVER` and `REPLACE_TRAEFIK_NETWORK` in `compose.traefik.yaml`, then:

```bash
docker compose -f compose.traefik.yaml up -d --build
```

| Path | Purpose |
| --- | --- |
| `public/` | The page, icons and self-hosted fonts |
| `nginx.conf` | Static serving, security headers, `/healthz` |
| `compose.traefik.yaml` | Traefik router for `jeux.jdelgado.fr` |

## License

Code: ISC. Fonts in `public/fonts/` (Bungee, Fredoka, Luckiest Guy): SIL Open Font License 1.1.
