# Altelink

Projet full-stack avec architecture MVC conteneurisée.

## Stack Technique

- **Frontend**: React.js
- **Backend**: Express.js + Node.js
- **Base de données**: PostgreSQL
- **Conteneurisation**: Docker & Docker Compose

## Structure du Projet

```
altelink/
├── backend/
│   ├── src/
│   │   ├── controllers/    # Logique métier
│   │   ├── models/         # Modèles de données
│   │   ├── views/          # Templates/réponses
│   │   ├── routes/         # Routes API
│   │   ├── config/         # Configuration (BDD, etc.)
│   │   └── middlewares/    # Middlewares Express
│   ├── server.js           # Point d'entrée backend
│   ├── Dockerfile
│   └── package.json
├── frontend/
│   ├── public/
│   ├── src/
│   │   ├── components/     # Composants réutilisables
│   │   ├── views/          # Pages/Vues
│   │   ├── services/       # Services API
│   │   └── utils/          # Utilitaires
│   ├── Dockerfile
│   └── package.json
├── docker-compose.yml
├── .env.example
└── README.md
```

## Prérequis

- Docker & Docker Compose (recommandé)
- Node.js 18+ (si installation sans Docker)
- PostgreSQL 15+ (si installation sans Docker)

## Installation

### Avec Docker (recommandé)

```bash
# 1. Configurer les variables d'environnement
cp .env.example .env
# Éditer .env avec vos valeurs

# 2. Lancer tous les services (PostgreSQL, Backend, Frontend)
docker compose up -d

# 3. Vérifier l'état des conteneurs
docker compose ps

# 4. Voir les logs en temps réel
docker compose logs -f

# 5. Arrêter les services
docker compose down

# 6. Supprimer les volumes (données)
docker compose down -v
```

### Sans Docker

#### 1. PostgreSQL
```bash
# Créer la base de données
createdb altelink
# ou via psql
psql -U postgres -c "CREATE DATABASE altelink;"
```

#### 2. Backend
```bash
cd backend
npm install
cp ../.env.example ../.env
# Configurer les variables d'environnement
npm run dev
```

#### 3. Frontend
```bash
cd frontend
npm install
npm start
```

## URLs des Services

- **Frontend**: http://localhost:3000
- **Backend API**: http://localhost:5000
- **PostgreSQL**: localhost:5432

## Commandes Utiles Docker

```bash
# Reconstruire les images
docker compose build

# Redémarrer un service spécifique
docker compose restart backend

# Accéder au shell d'un conteneur
docker compose exec backend sh
docker compose exec postgres psql -U altelink_user -d altelink

# Voir les logs d'un service
docker compose logs -f backend
```

## Variables d'Environnement

Voir `.env.example` pour la liste complète des variables requises.
