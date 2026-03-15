# TP .NET - API Todo (ESP 2025/2026)

## Description
API web ASP.NET Core 10.0 avec MongoDB, Docker et sécurisation Identity (rôles admin/user).  
Seul un **admin** peut ajouter/modifier/supprimer un Todo. Tous les utilisateurs authentifiés peuvent lire.

## Prérequis
- Docker Desktop
- .NET 10.0 SDK (pour développement local)

## Instructions d'exécution
### 1. Exécution locale
```bash
dotnet run

####L’API est accessible sur : https://localhost:7188/swagger
### Avec Docker 
```bash
docker build -t todoapi .
docker run -d -p 8080:8080 --name todoapi todoapi
L’API est accessible sur : http://localhost:8080/swagger
3. Tests de sécurité (JWT + Rôles)
Login :

POST /api/Auth/login

Utilisateurs :

Admin : { "username": "admin", "password": "password123" } → peut ajouter, modifier, supprimer
User : { "username": "user", "password": "user123" } → lecture seulement

Règles appliquées  :

GET /api/Todos → accessible à tout utilisateur identifié
POST / PUT / DELETE → seul rôle "admin"
