# Journal des décisions

| Date | Décision |
|---|---|
| 2026-11-24 | Le labo devient le **projet du jury RNCP36061** (mars 2027). Ajout d'une application à déployer (movie-service et cast-service du projet Jenkins) pour couvrir les compétences 5 et 8. Cluster API et autoscaling des VM classés en bonus. Voir `docs/rncp/`. |
| 2026-11-24 | Scénario de bascule vers AWS (pipeline DR, k3s sur EC2, Velero, ArgoCD, DNS) testé une fois par trimestre. Prérequis : miroir Git hors maison, 7 jours de sauvegardes en S3 Standard. |
| 2026-11-24 | AWS S3 (puis Glacier Deep Archive par cycle de vie) comme 3e copie des sauvegardes. Labos AWS jetables (`apply` / `destroy`) avec alerte de budget. Le tout-cloud est écarté : trop cher pour un labo allumé en permanence. |
| 2026-11-24 | Oracle a réduit son offre gratuite ARM à 2 OCPU / 12 Go (juin 2026). Passage prévu en compte PAYG (4 OCPU / 24 Go sans frais) avec alerte de budget. |
| 2026-11-24 | Architecture v2 : deux clusters Kubernetes séparés (maison et Oracle) synchronisés par ArgoCD, pas d'etcd partagé entre les sites ; la base reste à côté de son application. Voir `docs/architecture-hybride.md`. |
| 2026-11-24 | Matériel : mini PC fanless i5-1235U en DDR4 sur rail DIN (MNBOXCONET sous réserve de confirmation du vendeur, sinon CWWK 6 ports i226-V), 64 Go de RAM, Proxmox (pas Ubuntu en direct). Écartés : DDR5 (prix de la RAM), SFP+ (inutile avec la Freebox), PC industriels (prix). |
| 2026-11-05 | Dépôt GitHub `devopslab` en **public** (vitrine). Règles : pas de secrets, pas de tfstate, pas d'infos de repérage, gitleaks en pre-commit. `pi3-n8n` reste privé. |
| 2026-11-05 | Création du dossier `devopslab` pour garder les travaux de préparation. |
| 2026-11-05 | Feuille de route en 9 étapes rédigée (WSL2, CI, Ansible, Oracle + Terraform, migration n8n, Pi en sauvegarde, Proxmox, k3s, observabilité). |
| 2026-11-05 | Proxmox confirmé comme hyperviseur du labo, à piloter par Terraform et Ansible plutôt qu'à la souris. |
| 2026-11-05 | Objectif : pratiquer un maximum d'outils pour peu cher. Seule dépense prévue : un mini PC reconditionné et un disque USB. |
| 2026-11-05 | Mode bac à sable : discussion et préparation seulement. Pas encore de mini PC ni de compte cloud. |
