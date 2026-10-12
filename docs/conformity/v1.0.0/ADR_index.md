# ADR Index — Iris Classifier v1.0.0

## Objectif

Les Architecture Decision Records (ADR) permettent de conserver la justification
des principales décisions techniques du projet.

Cet index résume les décisions structurantes de la version `v1.0.0`.

## Liste des décisions

| ADR ID | Décision |
|---|---|
| ADR-001 | Utilisation de RandomForestClassifier |
| ADR-002 | Utilisation de MLflow pour la traçabilité de l'entraînement |
| ADR-003 | Utilisation de JSON Lines pour les logs d'audit |
| ADR-004 | Pseudonymisation des identifiants utilisateurs avec HMAC-SHA256 |
| ADR-005 | Exposition du modèle avec FastAPI |
| ADR-006 | Conteneurisation de l'API avec Docker |

## ADR-001 — RandomForestClassifier

### Décision

Utiliser `RandomForestClassifier` de scikit-learn pour classifier les fleurs Iris.

### Motivation

Le modèle est simple à entraîner, adapté à un problème de classification
tabulaire et suffisant pour les objectifs pédagogiques du projet.

### Alternatives envisagées

- régression logistique ;
- arbre de décision ;
- SVM.

### Conséquences

Le projet dispose d'un modèle simple permettant de concentrer l'exercice sur
la traçabilité, le MLOps et la conformité plutôt que sur la complexité du modèle.

---

## ADR-002 — MLflow

### Décision

Utiliser MLflow pour tracer les entraînements.

### Motivation

MLflow permet d'associer un entraînement à un identifiant unique et de conserver
des métadonnées utiles à la reproductibilité.

### Alternatives envisagées

- fichiers de métadonnées uniquement ;
- suivi manuel des expérimentations.

### Conséquences

Chaque modèle peut être relié à son `mlflow_run_id` et aux informations de son
entraînement.

---

## ADR-003 — Logs JSON Lines

### Décision

Stocker les événements d'audit au format JSON Lines (`.jsonl`).

### Motivation

Ce format est simple, structuré, lisible ligne par ligne et facilement exploitable
par des scripts.

### Alternatives envisagées

- fichier texte non structuré ;
- base de données ;
- plateforme centralisée de logging.

### Conséquences

La solution est adaptée à l'exercice mais devrait être réévaluée pour un système
distribué ou à fort volume.

---

## ADR-004 — Pseudonymisation HMAC-SHA256

### Décision

Pseudonymiser les identifiants utilisateurs avec HMAC-SHA256.

### Motivation

Éviter de conserver directement l'identifiant utilisateur tout en permettant
de corréler les événements associés à un même identifiant.

### Alternatives envisagées

- stockage de l'identifiant en clair ;
- hash simple ;
- suppression complète de l'identifiant.

### Conséquences

La confidentialité est améliorée, mais les données pseudonymisées restent à
protéger et ne doivent pas être considérées comme anonymes.

---

## ADR-005 — FastAPI

### Décision

Utiliser FastAPI pour exposer le modèle via une API HTTP.

### Motivation

FastAPI permet de construire simplement une API Python typée avec validation
des entrées et documentation OpenAPI/Swagger automatique.

### Alternatives envisagées

- Flask ;
- utilisation directe du modèle sans API.

### Conséquences

Le modèle peut être interrogé via `/predict` et testé avec Swagger.

---

## ADR-006 — Docker

### Décision

Conteneuriser l'API avec Docker.

### Motivation

Docker fournit un environnement d'exécution reproductible et facilite
l'intégration de l'application et de ses dépendances.

### Alternatives envisagées

- exécution Python directement sur l'hôte ;
- environnement virtuel uniquement.

### Conséquences

L'API peut être construite et exécutée dans un environnement isolé et
reproductible.
