# Projet AfricaShop - AWS Cloud Architecting (M1)

Ce dépôt contient l'infrastructure, le code et les livrables du projet de fin de module pour la plateforme e-commerce AfricaShop.

## 📂 Structure du dépôt
- `backend/` : Code de l'API FastAPI (Python, SQLAlchemy).
- `frontend/` : Code du site statique (HTML/CSS/JS).
- `infra/` : Templates CloudFormation (Starter et Architecture cible).
- `scripts/` : Scripts de déploiement et de publication.
- `loadtest/` : Script de test de charge (Locust).
- `livrables/` : Dossier d'architecture (PDF), schéma Draw.io, fichier YAML final et captures d'écran.

## 🚀 Déploiement de l'architecture cible (CloudFormation)

L'ensemble de l'infrastructure (VPC, ALB, Auto Scaling Group, RDS Multi-AZ, S3) est décrite en Infrastructure as Code (IaC).

### Prérequis :
- Un compte AWS (région `eu-west-3` Paris recommandée).
- Une paire de clés SSH créée dans EC2 (ex: `africashop-key`).
- Un bucket S3 unique pour les photos.

### Étapes :
1. Aller dans le service **CloudFormation** > **Créer une pile**.
2. Choisir **Importer un fichier de modèle** et sélectionner le fichier `livrables/africashop-final.yaml`.
3. Renseigner les paramètres demandés :
   - `KeyName` : Le nom de votre clé SSH.
   - `S3BucketName` : Le nom de votre bucket S3.
   - `DBPassword` : Un mot de passe sécurisé pour la base RDS.
4. Cocher la case autorisant la création de ressources IAM.
5. Soumettre et attendre le statut `CREATE_COMPLETE` (environ 15 minutes).

## 💻 Lancement de l'application en local

1. Se rendre dans le dossier `backend/`.
2. Créer un environnement virtuel : 
   ```bash
   python3 -m venv .venv
   source .venv/bin/activate  # (ou .venv\Scripts\activate sur Windows)
