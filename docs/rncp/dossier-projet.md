# Dossier de projet : squelette

Plan imposé par les modalités de validation du titre RNCP36061. À remplir au fil du projet, puis à exporter en PDF pour le dépôt à J-15.

Légende : ☐ à faire · ◐ en cours · ☑ terminé

## 1. Compétences du référentiel couvertes par le projet ◐

Reprendre le tableau de [competences.md](competences.md) une fois le projet terminé, avec pour chaque compétence la partie du projet qui la démontre et un renvoi vers la section « Réalisations ».

## 2. Cahier des charges ◐

Version finale de [cahier-des-charges.md](cahier-des-charges.md), avec les cibles chiffrées validées (SLA, RTO, RPO, budget).

## 3. Spécifications techniques ◐

- Schéma de l'infrastructure : [architecture-hybride.md](../architecture-hybride.md)
- Schéma de l'application à mettre en production (microservices, base, ingress) ☐
- Plan d'adressage et réseaux (VLAN, tunnel entre sites) ☐
- Dimensionnement des VM et des containers (CPU, RAM, disque) ☐
- Choix techniques justifiés, sous forme d'ADR : Proxmox, hybride, Oracle, AWS S3, Kubernetes, ArgoCD ☐

## 4. Démarche et outils ☐

- Méthode : itérations courtes, journal des décisions ([journal.md](../journal.md)), merge requests relues
- Outils par domaine : IaC (Terraform, Ansible), CI/CD (GitLab CI, Jenkins), containers (Docker, Kubernetes, Helm), GitOps (ArgoCD), données (PostgreSQL, CloudNativePG, Velero), supervision (Prometheus, Grafana, Alertmanager), sécurité (SOPS, cert-manager, Trivy)
- Collaborations : remontée des anomalies aux développeurs par les tickets GitLab

## 5. Réalisations ☐

Les scripts et configurations les plus significatifs, chacun argumenté (pourquoi ce choix, ce que ça garantit) :

- ☐ Module Terraform de création des VM Proxmox à partir du modèle cloud-init
- ☐ Rôle Ansible de durcissement (recommandations ANSSI)
- ☐ Script Python sur l'API Proxmox, script PowerShell de création d'une VM Windows
- ☐ Pipeline GitLab CI (tests, scan d'images, déploiement par environnement, approbation prod)
- ☐ Manifests Kubernetes : ressources, sondes, volumes, mises à jour progressives
- ☐ Cluster PostgreSQL répliqué et politique de sauvegarde
- ☐ Règles d'alerte et tableau de bord SLA
- ☐ Pipeline de bascule vers AWS et rapport du test (RTO et RPO mesurés)

## 6. Situation de travail ayant nécessité une recherche ☐

Une vraie difficulté rencontrée pendant le projet : le problème, les sources consultées (dont au moins une en anglais), les hypothèses testées, la solution retenue. Noter les candidats au fil de l'eau dans le journal.

## Diaporama (30 min) ☐

Canevas imposé :
1. Présentation de l'entreprise et/ou du service
2. Contexte du projet : cahier des charges, contraintes, livrables
3. Infrastructure déployée et application mise en production
4. Un exemple significatif du travail réalisé
5. Un exemple de recherche effectuée
6. Synthèse et conclusion : satisfactions et difficultés

Prévoir une vidéo de démonstration de secours, au cas où le réseau ferait défaut le jour J.
