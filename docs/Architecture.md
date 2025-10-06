# Architecture du projet

## Frontend (Vue.js)
- Authentification
- Espace Patient
- Espace Médecin
- Espace Laborantin
- Espace Secrétaire
- Espace Admin

## Backend (Django REST)
- API REST (patients, médecins, examens, résultats, factures, statistiques)
- Authentification JWT
- Génération et impression des résultats et les reçus de paiement
- Gestion des rôles et permissions

## Base de données
- PostgreSQL
- Modèles principaux :
  - Utilisateur / Rôle
  - Patient
  - Médecin
  - Analyse + Valeurs de référence
  - Rendez-vous
  - Examen
  - Résultat
  - Paiement
