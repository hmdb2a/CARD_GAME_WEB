# Jeu de cartes en ligne (PHP, MySQL, JavaScript)

Site web de jeu de cartes multijoueur avec inscription et connexion des joueurs, plateau de jeu en glisser-déposer et chat intégré.

Projet du module Programmation Web de la Licence Informatique (Université Paris-Saclay), réalisé en binôme.

## Fonctionnalités

- **Inscription et connexion** : formulaire avec contrôle des champs, vérification des doublons de nom d'utilisateur et mots de passe hachés (`password_hash`) en base MySQL
- **Plateau de jeu** : pioche et cartes déplaçables par glisser-déposer, distribution aléatoire des cartes, appels Ajax
- **Chat** entre joueurs, horodaté, développé comme un module séparé (`chat/`)

Les règles du jeu (un Huit américain) n'ont pas été implémentées, et deux joueurs ne partagent pas encore la même partie : voir la section limites du rapport.

## Technologies

PHP, MySQL, HTML, CSS (Bootstrap), JavaScript (jQuery, Ajax)

## Installation en local

1. Installer un serveur Apache et MySQL, par exemple [XAMPP](https://www.apachefriends.org/).
2. Créer la base de données et la table des joueurs :
   ```sql
   CREATE DATABASE game;
   USE game;
   CREATE TABLE users (
     user_id INT NOT NULL AUTO_INCREMENT PRIMARY KEY,
     username VARCHAR(32),
     email VARCHAR(40),
     password VARCHAR(255),
     experience VARCHAR(40)
   ) ENGINE=InnoDB DEFAULT CHARSET=utf8mb4;
   ```
3. Copier le dossier du projet dans la racine du serveur web (`htdocs` pour XAMPP).
4. Ouvrir `http://localhost/<nom-du-dossier>` dans un navigateur, créer un joueur avec **Register**, puis se connecter avec **Login**.

La connexion à la base se fait avec l'utilisateur `root` sans mot de passe (configuration par défaut de XAMPP), à adapter dans `game-mat.php` si besoin.

## Structure

| Élément | Rôle |
|---|---|
| `index.html` | Page d'accueil : inscription et connexion |
| `game-mat.php` | Traitement des formulaires, accès à la base, plateau de jeu |
| `logout.php` | Déconnexion |
| `chat/` | Publication et affichage des messages |
| `css/`, `js/`, `images/` | Styles, bibliothèques JavaScript, images des cartes |
| `docs/Rapport.pdf` | Rapport du projet |

## Auteurs

Ahmed Baaroun, Hilmi Celayir
