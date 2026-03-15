# TP .NET - API Todo (ESP 2025/2026)

## Description
API web ASP.NET Core 10.0 avec MongoDB, Docker et sécurisation Identity (rôles admin/user).  
Seul un **admin** peut ajouter/modifier/supprimer un Todo. Tous les utilisateurs authentifiés peuvent lire.

## Prérequis
- Docker Desktop
- .NET 10.0 SDK (pour développement local)

```markdown

## Exécution

### 1. Lancement local
```bash
dotnet run
```

### 2. Avec Docker
```bash
docker build -t todoapi .
docker run -d -p 8080:8080 --name todoapi todoapi
```

### 3. Tests d’authentification (Postman)

**Login Admin**
```bash
POST http://localhost:8080/api/auth/login
```
```json
{
  "email": "admin@example.com",
  "password": "AdminPass123!"
}
```

**Login User**
```bash
POST http://localhost:8080/api/auth/login
```
```json
{
  "email": "user@test.com",
  "password": "Pass123!"
}
```

### 4. Règles de sécurité appliquées
- `GET /api/todos` → accessible à tout utilisateur identifié  
- `POST / PUT / DELETE /api/todos` → uniquement rôle **admin**

---
