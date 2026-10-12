# Release Memo — Iris Classifier v1.0.0

## Informations générales

| Élément | Valeur |
|---|---|
| Version | 1.0.0 |
| Modèle | RandomForestClassifier |
| Dataset | Iris |
| Model version | iris-v1 |
| MLflow Run ID | 4ac329e26aa84b666be481dbccebba412 |
| Git SHA entraînement | abc1234 |
| Tracking | MLflow |

## Changements introduits

Cette release intègre les éléments développés dans les chapitres précédents :

- entraînement et évaluation du modèle Iris ;
- traçabilité de l'entraînement avec MLflow ;
- documentation du modèle avec une Model Card ;
- exposition du modèle via une API FastAPI ;
- journalisation structurée des prédictions ;
- attribution d'un `request_id` aux prédictions ;
- pseudonymisation des identifiants utilisateurs ;
- reconstruction d'une prédiction avec `audit_query.py` ;
- documentation de conformité centralisée et versionnée.

## Performances

Lors de l'entraînement associé à cette version :

**Accuracy : 1.0000**

Le résultat correspond au run MLflow référencé dans les métadonnées du modèle.

Pour le détail des performances et des limites :

[Model Card](./model_card.md)

## Améliorations

Cette version apporte principalement des améliorations de gouvernance et
de traçabilité :

- association modèle / MLflow / Git ;
- audit trail des prédictions ;
- documentation centralisée ;
- classification du risque AI Act ;
- séparation des secrets et du code source.

## Régressions connues

Aucune régression fonctionnelle n'a été identifiée dans le cadre des tests
réalisés pour cet exercice.

Cette conclusion est limitée au périmètre pédagogique et aux tests effectués.

## Classification du risque

Voir :

[Risk Classification](./risk_classification.md)

## Auditabilité

Voir :

[Audit Trail](./audit_trail_README.md)

## Décision de release

**Décision : ACCEPTÉE POUR LE CONTEXTE PÉDAGOGIQUE**

La version `v1.0.0` est considérée comme suffisamment documentée et traçable
pour servir de release de référence dans le cadre de cet exercice.

Cette décision ne constitue pas une autorisation de déploiement dans un
contexte réel ou sensible. Un changement de cas d'usage nécessiterait une
nouvelle évaluation du risque et de la conformité.
