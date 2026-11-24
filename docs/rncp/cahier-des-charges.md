# Cahier des charges (premier jet)

Version de travail du 24/11/2026, à compléter et valider. Le contexte d'entreprise est fictif, inspiré d'une PME industrielle réelle : aucun nom ni information permettant d'identifier une entreprise ou un lieu.

## 1. Contexte

**L'entreprise.** PME industrielle d'environ 110 utilisateurs, avec un service informatique réduit qui gère à la fois l'IT de gestion et l'informatique d'atelier.

**L'existant.** Infrastructure sur site virtualisée (hyperviseur, une vingtaine de VM Windows et Linux), ERP en SaaS, applications métier internes. Les déploiements se font à la main, la documentation est dispersée et la reprise après sinistre n'a jamais été testée.

**Le besoin.** L'équipe de développement interne livre une application web (microservices Python/FastAPI avec base PostgreSQL). La direction veut :
- des mises en production plus fréquentes et sans interruption ;
- une infrastructure reconstructible automatiquement ;
- un deuxième site dans le cloud pour la continuité de service ;
- une supervision avec des engagements de service mesurables.

## 2. Objectifs

1. Décrire toute l'infrastructure en code, versionné dans Git (Terraform, Ansible, manifests Kubernetes).
2. Déployer l'application sur quatre environnements : dev, qa, staging (identique à la prod) et prod.
3. Automatiser la mise en production par une pipeline CI/CD et le GitOps.
4. Assurer la continuité : site secondaire dans le cloud, sauvegardes 3-2-1, plan de reprise testé.
5. Superviser les services avec des indicateurs liés aux SLA et à la sécurité.

## 3. Périmètre

**Inclus :** site principal sur site (hyperviseur Proxmox), site secondaire Oracle Cloud, stockage de sauvegarde AWS S3, pipeline CI/CD, cluster Kubernetes, base de données répliquée, supervision et alertes, durcissement de sécurité, documentation d'exploitation.

**Exclus :** développement de l'application (fournie par l'équipe de développement), haute disponibilité matérielle du site principal (une seule machine physique), migration de l'existant de production.

## 4. Exigences fonctionnelles

| Réf. | Exigence |
|---|---|
| EF1 | Une VM supprimée par erreur est recréée automatiquement depuis le code |
| EF2 | Un commit validé sur la branche principale déploie automatiquement en dev et qa ; la prod demande une approbation manuelle |
| EF3 | Chaque environnement est isolé (namespace, base de données, secrets) |
| EF4 | L'application reste disponible si un nœud Kubernetes tombe |
| EF5 | Les services permanents continuent sur le site cloud si le site principal tombe |
| EF6 | Une alerte prévient l'exploitant en cas d'indisponibilité, de saturation ou d'échec de sauvegarde |

## 5. Exigences non fonctionnelles

| Réf. | Exigence | Cible à valider |
|---|---|---|
| ENF1 | Disponibilité de l'application en prod | à définir (ex. 99,5 % mensuel) |
| ENF2 | RTO en cas de perte du site principal | à mesurer lors du test de bascule |
| ENF3 | RPO de la base de données | à mesurer (réplication asynchrone) |
| ENF4 | Sécurité | recommandations ANSSI GNU/Linux, accès par clé, pare-feu, TLS partout, secrets chiffrés, moindre privilège |
| ENF5 | Coût cloud | budget mensuel plafonné, avec alertes |
| ENF6 | Traçabilité | toute modification passe par une merge request relue |

## 6. Contraintes

- Une seule machine physique sur site : mini PC fanless sur rail DIN, 64 Go de RAM.
- Budget matériel limité ; services cloud en offre gratuite ou au plus bas coût.
- Lien Internet grand public (débit montant limité) entre les sites.
- Site cloud en architecture ARM : images de containers multi-architecture.

## 7. Livrables

- Dépôt Git complet : code d'infrastructure, pipelines, manifests, documentation.
- Schéma d'architecture et dossier de spécifications techniques.
- Runbooks d'exploitation : déploiement, restauration, bascule.
- Tableaux de bord de supervision et règles d'alerte.
- Rapport du test de bascule (RTO et RPO mesurés).

## 8. Critères de réception

- Destruction puis recréation complète d'un environnement à partir du code, sans action manuelle.
- Déploiement d'une nouvelle version de l'application de dev jusqu'en prod par la pipeline.
- Test de bascule réalisé et chronométré.
- Restauration complète d'une sauvegarde réussie.
- Alertes déclenchées et reçues lors de pannes simulées.
