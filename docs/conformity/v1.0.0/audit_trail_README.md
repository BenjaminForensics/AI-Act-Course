# Audit Trail — Iris Prediction API

## Objectif

Le système conserve un audit trail permettant de retracer les prédictions
effectuées par l'API Iris.

Chaque prédiction reçoit un `request_id` unique permettant de retrouver
ultérieurement les informations associées.

## Événements et informations enregistrés

Pour chaque prédiction, le journal d'audit contient notamment :

- `request_id`
- `model_version`
- `git_sha`
- `mlflow_run_id`
- `prediction`
- `confidence`
- `latency_ms`
- `user_id_pseudo`

Les données brutes d'entrée et le `user_id` original ne sont pas enregistrés
dans le journal d'audit.

## Stockage des logs

Les événements sont enregistrés au format JSON Lines dans :

`logs/audit.jsonl`

Chaque ligne correspond à un événement indépendant.

Le fichier de logs est un artefact d'exécution local et n'est pas versionné
dans Git.

## Pseudonymisation

L'identifiant utilisateur n'est jamais enregistré en clair.

Il est pseudonymisé à l'aide de HMAC-SHA256 avec une clé secrète
gérée séparément du code source.

La clé secrète n'est ni enregistrée dans les logs ni versionnée
dans le repository Git.

## Reconstitution d'une prédiction

Une décision peut être recherchée à partir de son `request_id` avec :

```bash
uv run src/audit_query.py --request_id <REQUEST_ID>
