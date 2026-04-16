# Projet Cirrus : Modernisation et Migration Cloud (Nimbus Corp)
## 📋 Présentation du Projet
Le **projet Cirrus** consiste en la conception et la mise en œuvre d'une **infrastructure Cloud** native pour la société **Nimbus Corp** (80 collaborateurs). L'objectif principal était de **migrer** une **application** métier critique et une **base de données** d'un environnement *On-Premise* obsolète vers une architecture **AWS** hautement disponible, sécurisée et souveraine.

## -------- Livrables du Projet -------- 
### 📂 [Livrable 1 : Analyse de l'Infrastructure et des Besoins](./livrables/Rousseau_Alexis_1_analyse_de_besoin_042026.pdf)
Ce document définit le périmètre technique et les objectifs métiers de la migration.

- **Audit de l'existant** : Identification des points de défaillance uniques (SPOF) sur l'infrastructure physique.

- **Expression des besoins** : Latence utilisateur < 50ms (Optimisation pour le télétravail).

- **Disponibilité** de service (**SLA**) de 99,9%.

- **Gestion hybride** pour un NAS de 12 To d'archives.

- **Analyse de risques** : Matrice de criticité (Perte de données, intrusion, interruption de service).

### 📂 [Livrable 2 : Rapport de Veille Technologique](./livrables/Rousseau_Alexis_2_rapport_veille_042026.pdf)
Étude comparative et justification des choix technologiques face aux enjeux de Nimbus Corp.

- **Comparaison des fournisseurs** : Benchmark **AWS** vs **Azure** vs **GCP** vs **OVHcloud** vs **SCALEWAY** (*Critères* : Souveraineté, services managés, TCO).

- **Choix de la Région** : Sélection de Paris (*eu-west-3*) pour la conformité RGPD et la latence minimale.

- **Enseignements clés** : Adoption du modèle Serverless (Fargate) pour réduire la dette opérationnelle et du stockage gp3 pour l'efficience économique.

### 📂 [Livrable 3 : Document d'Architecture Technique (DAT)](./livrables/Rousseau_Alexis_3_document_architecture_042026.pdf)
Conception détaillée de la cible **AWS** (Phase 1).

- **Architecture Réseau** : VPC segmenté en 3 couches (Public, App, Data) sur 2 Zones de Disponibilité (Multi-AZ).

- **Calcul & Data** : Cluster ECS Fargate (Actif/Actif) et RDS PostgreSQL Multi-AZ (Réplication synchrone).

- **Sécurité Zero Trust** : Mise en œuvre d'AWS WAF, d'une authentification forte via Amazon Cognito (MFA) et chiffrement KMS des données au repos.

- **Hybridation** : Mise en place d'un VPN Site-to-Site entre le Fortigate local et le Cloud AWS.

## -------- Stack Technique -------- 
- **Cloud Provider** : AWS (Région Paris)

- **Compute** : AWS Fargate (Docker)

- **Base de données** : Amazon RDS (PostgreSQL)

- **Cache** : Amazon ElastiCache (Redis 7.0)

- **Réseau** : VPC, ALB, NAT Gateway, Site-to-Site VPN

- **Sécurité** : AWS WAF, AWS Shield, KMS, Amazon Cognito, IAM

- **Infrastructure as Code**: Terraform (State stocké sur S3 avec verrouillage DynamoDB)

- **Supervision** : Amazon CloudWatch, AWS CloudTrail, GuardDuty

## -------- Optimisation FinOps -------- 
L'architecture a été conçue pour respecter une enveloppe budgétaire optimisée :

- **Modèle de facturation** : Utilisation de Savings Plans (Compute) et d'instances réservées (RDS).

- **Cible budgétaire** : ~800 € / mois (TCO incluant support et connectivité).

- **Cycle de vie** : Politiques d'archivage automatique vers S3 Glacier pour la Phase 2.

## -------- Résilience et Sécurité -------- 
- **Haute Disponibilité** : Basculement automatique (Failover) en moins de 60 secondes en cas de panne de zone.

- **Sauvegardes** : Stratégie de backup automatisée et immuable via AWS Backup.

- **Conformité** : Alignement sur les standards ISO 27001/27017/27018 et les recommandations de l'ANSSI.

## Auteur
Rousseau Alexis - Administrateur Système - Architecte Cloud

Projet réalisé dans le cadre de la **modernisation** de l'infrastructure de **Nimbus Corp**.