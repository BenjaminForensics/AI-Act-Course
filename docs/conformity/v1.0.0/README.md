# Dossier de conformité — Iris Classifier v1.0.0

## Présentation du système

Iris Classifier est un système de classification basé sur un modèle
RandomForestClassifier.

Il prédit l'espèce d'une fleur Iris à partir de quatre caractéristiques
mesurées sur ses sépales et ses pétales.

Ce projet est utilisé dans un contexte pédagogique pour mettre en pratique
la documentation, la traçabilité et la gouvernance d'un système de machine
learning.

Documentation détaillée :

[Model Card](./model_card.md)

## Classification AI Act

Dans le contexte pédagogique actuel, le système est classé comme :

**Risque minimal**

L'analyse complète et les conditions nécessitant une réévaluation sont
documentées ici :

[Risk Classification](./risk_classification.md)

## Responsabilité

Dans le cadre de cet exercice, le rôle étudié est principalement celui de
**provider (fournisseur)** du système d'IA.

Les responsabilités doivent être réévaluées si le système est utilisé ou
déployé dans un autre contexte.

## Traçabilité

Les prédictions effectuées par l'API sont journalisées afin de permettre
leur traçabilité.

Chaque prédiction possède un `request_id` permettant de retrouver notamment :

- la prédiction produite ;
- la version du modèle ;
- le run MLflow associé ;
- la révision Git du code ;
- le pseudonyme utilisateur ;
- la latence de la requête.

Documentation :

[Audit Trail](./audit_trail_README.md)

## Documents de conformité

- [Model Card](./model_card.md)
- [Classification du risque](./risk_classification.md)
- [Audit Trail](./audit_trail_README.md)
- [Release Memo](./release_memo.md)
- [ADR Index](./ADR_index.md)

## Version

Dossier de conformité : **v1.0.0**
