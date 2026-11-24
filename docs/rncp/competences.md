# Projet RNCP : compétences et modalités

Titre visé : **Administrateur Système DevOps, RNCP36061, niveau 6** (code titre TP-01414). Jury : mars 2027, à Paris.

## L'épreuve (2 h 05)

| Épreuve | Durée | Ce qui est évalué |
|---|---|---|
| Questionnaire professionnel écrit, en anglais | 30 min | CP11 : lire un document technique en anglais et répondre par écrit |
| Présentation du projet | 45 min, dont 15 min de lecture du dossier par le jury | Le projet, sur diaporama |
| Entretien technique | 30 min | Le projet, puis les compétences qu'il ne couvre pas |
| Entretien final | 20 min | Dossier professionnel |

À déposer **en PDF au plus tard J-15** : le dossier professionnel et le dossier projet. Le jour J : diaporama, ordinateur portable, convocation, pièce d'identité.

Compétences **obligatoires** dans le projet : CP2, CP7, CP10.

## Correspondance avec le projet

| CP | Compétence | Ce qui la couvre | État |
|---|---|---|---|
| 1 | Automatiser la création de serveurs à l'aide de scripts | Modèles cloud-init, Terraform | À compléter : un script Python (API Proxmox) et un script PowerShell (VM Windows), le référentiel cite bash, PowerShell et Python |
| 2 ★ | Automatiser le déploiement d'une infrastructure | Terraform + Ansible + GitLab CI | Couvert |
| 3 | Sécuriser l'infrastructure | IAM, secrets chiffrés | À compléter : recommandations ANSSI GNU/Linux (rôle Ansible), authentification par clé, pare-feu, certificats (cert-manager), tests des mises à jour en préproduction |
| 4 | Mettre l'infrastructure en production dans le cloud | Oracle et AWS en Terraform | Couvert |
| 5 | Préparer un environnement de test | Application en dev et qa | **Manque l'application** : reprendre movie-service et cast-service (projet Jenkins) |
| 6 | Gérer le stockage des données | PostgreSQL, CloudNativePG (réplication), Velero, S3 | Couvert |
| 7 ★ | Gérer des containers | Kubernetes, limites CPU et mémoire, volumes, mises à jour | Couvert |
| 8 | Automatiser la mise en production avec une plateforme | Kubernetes + ArgoCD, staging identique à la prod | Dépend de l'application |
| 9 | Définir et mettre en place des statistiques de services | Grafana | À compléter : indicateurs liés aux SLA, indicateurs de sécurité (accès, intrusions) |
| 10 ★ | Exploiter une solution de supervision | Prometheus, Grafana, Alertmanager, agents sur tous les nœuds | À compléter : flux de supervision chiffrés (TLS) |
| 11 | Échanger sur des réseaux professionnels, éventuellement en anglais | Questionnaire écrit | Révision séparée, plus la situation de recherche du dossier |

## Critères de performance à démontrer

- **CP1** : le serveur est fonctionnel, conforme au cahier des charges, documentation à jour.
- **CP2** : serveurs fonctionnels, architecture conforme, scripts documentés.
- **CP3** : mises à jour testées avant déploiement, accès aux serveurs sécurisés.
- **CP4** : serveurs accessibles par les utilisateurs finaux, architecture documentée.
- **CP5** : version de test produite, tests effectués, dysfonctionnements remontés aux développeurs.
- **CP6** : serveurs de données opérationnels, droits conformes, données sauvegardées.
- **CP7** : containers opérationnels, connectés au réseau et au stockage distant, mis à jour.
- **CP8** : préproduction conforme à la production, containers décrits sur la plateforme, application disponible.
- **CP9** : indicateurs pertinents, exhaustifs, tenant compte des SLA.
- **CP10** : indicateurs pertinents, alertes correctement interprétées, échanges réguliers avec les développeurs.

## Règle de préparation

Ne présenter que ce que je peux expliquer sans notes. Cluster API et l'autoscaling des VM restent en **bonus** : montrés s'ils sont prêts, sinon Terraform avec détection d'écarts couvre la reconstruction automatique.

## Calendrier

| Période | Objectif |
|---|---|
| Décembre 2026 | Commander la machine. Proxmox, Terraform, Ansible (durcissement ANSSI), GitLab CI. Premier jet du cahier des charges |
| Janvier 2027 | Kubernetes, application en dev/qa/staging/prod, ArgoCD, PostgreSQL répliqué, supervision (SLA + sécurité), site Oracle |
| Début février 2027 | Sauvegardes S3, test de bascule chronométré. **Gel des fonctionnalités** |
| Mi-février 2027 | Dossier projet et dossier professionnel finalisés, **dépôt à J-15** |
| Fin février – mars 2027 | Diaporama, vidéo de démo de secours, oraux blancs, révision de l'anglais |
