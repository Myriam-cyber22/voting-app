# Voting App

Application de vote distribuée containerisée avec Docker.

## Prérequis

- Docker
- Docker Compose

## Lancer le projet
```bash
docker compose up --build
```

## Accéder aux applications

| Application | URL |
|-------------|-----|
| Vote | http://localhost:8080 |
| Résultats | http://localhost:8081 |

## Architecture

| Service | Rôle |
|---------|------|
| vote | Application web Python - interface de vote |
| result | Application web Node.js - affichage des résultats |
| worker | Service .NET - traitement des votes |
| redis | File de messages entre vote et worker |
| db | Base de données PostgreSQL |

## Modifications apportées au code source

- `result/server.js` : hostname PostgreSQL déjà configuré sur `db`
- `vote/app.py` : hostname Redis changé de `localhost` vers `redis`
- `worker/Program.cs` : hostnames Redis et PostgreSQL changés vers `redis` et `db`
- Dossier `run/` supprimé, remplacé par Docker Compose

## Arrêter le projet
```bash
docker compose down
```

## Arrêter et supprimer les données
```bash
docker compose down -v
```