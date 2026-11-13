# Deep-Pass — Gestionnaire de Mots de Passe Sécurisé

**Deep-Pass** est un gestionnaire de mots de passe moderne, **100% hors-ligne** et hautement sécurisé, conçu spécialement pour Windows 11 et Windows 10.

Reprenez le contrôle de vos données : aucun mot de passe n'est envoyé sur Internet, aucune télémétrie n'est collectée. Votre coffre-fort vous appartient et reste sur votre PC.

---

## Fonctionnalités Principales

*   **Sécurité de niveau militaire** : Vos données sont chiffrées avec **AES-256-GCM** et protégées par votre mot de passe maître (dérivation **Argon2id**).
*   **Interface Premium** : 8 thèmes visuels dégradés (Rouge Rubis, Vert Émeraude, Rose Néon...) et 5 fonds d'écran intégrés. L'interface s'adapte à la taille de police que vous choisissez.
*   **Générateur de mots de passe** : Créez des mots de passe ultra-forts en un clic.
*   **Support 2FA / TOTP** : Stockez vos clés de double authentification et visualisez les codes à 6 chiffres en temps réel.
*   **Scanner de fuites (HIBP)** : Vérifiez si vos mots de passe ont fuité sur Internet (via l'API sécurisée HaveIBeenPwned).
*   **Tableau de Bord de Sécurité** : Obtenez un score sur 100 et identifiez vos mots de passe faibles, réutilisés ou trop anciens.
*   **Multi-format** : Importez et exportez facilement votre coffre en **PDF, JSON, CSV ou TXT**.
*   **Mode System Tray** : Réduisez l'application à côté de l'horloge Windows pour y accéder à tout moment.
*   **Copie en un clic** : Cliquez directement sur un champ pour le copier. L'URL s'ouvre dans votre navigateur.

---

## Raccourcis Clavier

Gagnez du temps avec ces raccourcis intégrés :

| Action | Raccourci |
| :--- | :--- |
| **Nouveau Compte** | `Ctrl + N` |
| **Nouvelle Catégorie** | `Ctrl + Shift + N` |
| **Exporter le Coffre-fort** | `Ctrl + E` |
| **Importer des Comptes** | `Ctrl + I` |
| **Masquer / Démasquer les mots de passe** | `Ctrl + H` |
| **Verrouiller immédiatement** | `Ctrl + L` |
| **Tableau de Bord de Sécurité** | `Ctrl + Shift + S` |
| **Vérifier les Fuites (HIBP)** | `Ctrl + Shift + F` |
| **Réinitialiser le Coffre-fort** | `Ctrl + Shift + R` |

---

## 🔒 Comment fonctionne la sécurité ?

Deep-Pass est conçu selon la philosophie **Zero-Knowledge** (Zéro Connaissance).
1.  Vous créez un mot de passe maître robuste.
2.  Ce mot de passe est transformé (haché avec Argon2id) pour créer une clé unique.
3.  Cette clé sert à chiffrer vos données locales (AES-256-GCM).
4.  **Le mot de passe maître n'est jamais stocké en clair.** Si vous le perdez, vos données sont irrécupérables. C'est le prix de la sécurité maximale.

---

## Installation

1.  Rendez-vous dans la section **Releases** (à droite sur GitHub).
2.  Téléchargez la dernière version de **`Deep-Pass.exe`**.
3.  Placez le fichier où vous le souhaitez (sur votre Bureau, par exemple).
4.  Double-cliquez pour lancer l'application. Aucune installation n'est nécessaire.

---

## ⚠️ Avertissement important pour vos données

Vos données sont précieusement conservées dans votre dossier utilisateur Windows :
`%APPDATA%\Deep-Pass\vault.db`

**Pensez à sauvegarder régulièrement ce fichier `vault.db`** (sur une clé USB, un disque dur externe, ou dans un cloud sécurisé). En cas de plantage de votre PC, ce fichier est votre seul moyen de retrouver vos mots de passe.