# Classification du risque AI Act — Iris Classifier

## Système concerné

Le système est un modèle RandomForestClassifier entraîné sur le dataset Iris.

Il prédit la classe d'une fleur à partir de quatre caractéristiques :
- longueur du sépale ;
- largeur du sépale ;
- longueur du pétale ;
- largeur du pétale.

Le système est développé dans un contexte pédagogique afin d'étudier le MLOps,
la traçabilité et la conformité des systèmes d'intelligence artificielle.

## Niveau de risque

**Risque minimal**

## Justification

Le système ne prend pas de décision concernant une personne physique.

Il n'est pas utilisé pour :
- le recrutement ou l'emploi ;
- l'éducation ou l'admission ;
- l'accès au crédit ou à des services essentiels ;
- la santé ;
- la biométrie ;
- l'application de la loi ;
- la migration ou le contrôle aux frontières ;
- l'administration de la justice.

Il ne met pas non plus en œuvre les pratiques interdites étudiées dans le cadre
de l'AI Act.

Dans le contexte pédagogique actuel, le système est donc considéré comme un
système à risque minimal.

Cette classification devrait être réévaluée si le modèle, ses données ou son
cas d'usage étaient modifiés.

## Rôle de l'organisation

Dans le cadre de cet exercice, le projet développe et met à disposition le
système d'IA.

Le rôle étudié est principalement celui de **provider (fournisseur)**.

Dans un déploiement réel, les rôles de provider et de deployer devraient être
déterminés selon les responsabilités effectives des organisations impliquées.

## Obligations principales

Compte tenu du cas d'usage pédagogique et de la classification retenue, le
système n'est pas traité dans cet exercice comme un système d'IA à haut risque.

Le projet applique néanmoins volontairement plusieurs bonnes pratiques de
gouvernance :

1. documentation du modèle avec une Model Card ;
2. versionnement du code et de la documentation avec Git ;
3. traçabilité de l'entraînement avec MLflow ;
4. journalisation des prédictions ;
5. pseudonymisation des identifiants utilisateurs ;
6. possibilité de reconstituer une prédiction à partir d'un `request_id`.

## Réévaluation du risque

La classification doit être revue en cas de modification :
- du cas d'usage ;
- des utilisateurs concernés ;
- des données utilisées ;
- des décisions prises à partir des prédictions ;
- ou du contexte de déploiement.
