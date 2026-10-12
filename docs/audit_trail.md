# Politique d'audit et de logging

## Données collectées

Les logs d'audit contiennent les informations suivantes :

- `request_id` : identifiant unique permettant de retrouver une prédiction.
- `model_version` : version du modèle ayant effectué la prédiction.
- `git_sha` : version du code source associée au modèle.
- `mlflow_run_id` : identifiant du run d'entraînement MLflow.
- `prediction` : résultat produit par le modèle.
- `confidence` : score de confiance associé à la prédiction.
- `latency_ms` : temps nécessaire pour produire la prédiction.
- `user_id_pseudo` : identifiant utilisateur pseudonymisé.

L'identifiant utilisateur réel n'est pas conservé dans les logs. Les données brutes
d'entrée ne sont pas enregistrées afin de respecter le principe de minimisation
des données.

## Finalité du traitement

Les logs sont collectés afin de permettre :

- la traçabilité des prédictions ;
- l'audit du système ;
- le diagnostic des erreurs ;
- la détection et l'analyse d'incidents ;
- la vérification de la conformité réglementaire.

## Base légale (RGPD)

Le traitement des logs peut reposer sur l'article 6.1.f du RGPD lorsque le logging
répond à l'intérêt légitime de l'organisation, notamment pour assurer la sécurité,
la traçabilité et le bon fonctionnement du système.

Lorsque la conservation des logs constitue une obligation réglementaire,
l'article 6.1.c du RGPD relatif au respect d'une obligation légale peut également
être applicable.

Pour les systèmes d'IA à haut risque, l'AI Act prévoit des exigences de logging
et de traçabilité.

## Durée de conservation

Pour cet exercice, une durée de conservation de 6 mois est retenue.

Cette durée permet de conserver un historique suffisant pour les besoins
d'audit, d'investigation et de conformité tout en limitant la conservation
des données.

## Protection des données

Les `user_id` ne sont jamais stockés directement dans les logs.

Ils sont transformés à l'aide de HMAC-SHA256 avec une clé secrète stockée dans
une variable d'environnement. Les logs contiennent uniquement le résultat
pseudonymisé dans le champ `user_id_pseudo`.

La pseudonymisation permet de reconnaître les requêtes appartenant au même
utilisateur sans stocker directement son identifiant.

Elle est différente de l'anonymisation : une donnée pseudonymisée reste une
donnée personnelle au sens du RGPD, alors qu'une donnée correctement anonymisée
ne permet plus de retrouver la personne concernée.

## Droits des utilisateurs

Les utilisateurs peuvent exercer les droits prévus par le RGPD, notamment les
droits d'accès, de rectification et, lorsque les conditions sont réunies,
d'effacement.

L'organisation doit être capable d'identifier les logs associés à un utilisateur
à partir du mécanisme de pseudonymisation afin de traiter ces demandes.

Les utilisateurs doivent également être informés de la collecte des logs, de
leur finalité et de leur durée de conservation.
