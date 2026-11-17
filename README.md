# Deep-Pass — Gestionnaire de Mots de Passe Sécurisé

**Deep-Pass** est un gestionnaire de mots de passe moderne, **100% hors-ligne** et hautement sécurisé, conçu spécialement pour Windows 11 et Windows 10.

Reprenez le contrôle de vos données : aucun mot de passe n'est envoyé sur Internet, aucune télémétrie n'est collectée. Votre coffre-fort vous appartient et reste sur votre PC.

---

## Fonctionnalités Principales

*   **Sécurité de niveau militaire** : Vos données sont chiffrées avec **AES-256-GCM** et protégées par votre mot de passe maître (dérivation **Argon2id**).
*   **Interface Premium** : 8 thèmes visuels dégradés (Rouge Rubis, Vert Émeraude, Rose Néon...) et 5 fonds d'écran intégrés. L'interface s'adapte à la taille de police que vous choisissez.
*   **Générateur de mots de passe** : Créez des mots de passe ultra-forts en un clic.
*   **Support 2FA / TOTP** : Stockez vos clés de double authentification et visualisez les codes à 6 chiffres en temps réel.
*   **Scanner de fuites (HIBP)** : Vérifiez si vos mots de passe ont fuité sur Internet (via l'API sécurisée HaveIBeenPwned, dans le respect total de votre anonymat).
*   **Tableau de Bord de Sécurité** : Obtenez un score sur 100 et identifiez vos mots de passe faibles, réutilisés ou trop anciens.
*   **Multi-format** : Importez et exportez facilement votre coffre en **PDF, JSON, CSV ou TXT**.
*   **Export / Import `.vaultpack`** : Exportez votre coffre complet (chiffré) pour le transférer sur votre téléphone Android, et importez un coffre depuis Android vers votre PC. **"App Android en Création..."**
*   **Mode System Tray** : Réduisez l'application à côté de l'horloge Windows pour y accéder à tout moment.
*   **Copie en un clic** : Cliquez directement sur un champ pour le copier. L'URL s'ouvre dans votre navigateur.

---

## 📋 Raccourcis Clavier & Options de Menus

| Action | Raccourci | Description |
| :--- | :--- | :--- |
| **Nouveau Compte** | `Ctrl + N` | Ouvre le formulaire de création de compte |
| **Nouvelle Catégorie** | `Ctrl + Shift + N` | Crée une catégorie sur-mesure |
| **Exporter le Coffre-fort** | `Ctrl + E` | Exporte le coffre (JSON, CSV, TXT, PDF) |
| **Exporter en .vaultpack** | `Ctrl + Shift + E` | Exporte l'archive sécurisée multi-plateforme |
| **Importer des Comptes** | `Ctrl + I` | Importe des comptes (JSON, CSV, TXT) |
| **Importer un .vaultpack** | `Ctrl + Shift + I` | Importe et restaure une archive `.vaultpack` |
| **Masquer / Démasquer les données** | `Ctrl + H` | Bascule l'affichage global de toutes les données sensibles |
| **Verrouiller le coffre-fort** | `Ctrl + L` | Verrouille immédiatement la session |
| **Tableau de Bord de Sécurité** | `Ctrl + Shift + A` | Ouvre l'audit de sécurité et score /100 |
| **Vérifier les Fuites (HIBP)** | `Ctrl + Shift + F` | Analyse les mots de passe contre HaveIBeenPwned |
| **Réinitialiser le Coffre-fort** | `Ctrl + Shift + R` | Réinitialise complètement le coffre-fort |
| **Préférences & Paramètres** | `Ctrl + P` | Ouvre la fenêtre des thèmes et de configuration |

---

## 🔒 Comment fonctionne la sécurité ?

Deep-Pass est conçu selon la philosophie **Zero-Knowledge** (Zéro Connaissance).
1.  Vous créez un mot de passe maître robuste.
2.  Ce mot de passe est transformé (haché avec Argon2id) pour créer une clé unique.
3.  Cette clé sert à chiffrer vos données locales (AES-256-GCM).
4.  **Le mot de passe maître n'est jamais stocké en clair.** Si vous le perdez, vos données sont irrécupérables. C'est le prix de la sécurité maximale.

**Le fichier `config.json` ne contient PAS votre clé de chiffrement.** Il contient uniquement le sel et un hash de vérification. La clé AES est recalculée à chaque connexion en RAM, à partir de votre mot de passe maître. Même avec `vault.db` + `config.json`, un attaquant ne peut rien faire sans votre mot de passe maître.

### 🌐 Et le scanner de fuites (HIBP) ?

Deep-Pass ne transmet **aucune donnée** sur Internet. La seule exception est le **scanner de fuites**, que vous devez **lancer manuellement**.

**Ce qui est envoyé à l'API Have I Been Pwned :**
- Uniquement les **5 premiers caractères** du hash SHA-1 de votre mot de passe.

**Ce qui n'est JAMAIS envoyé :**
- Votre mot de passe en clair.
- Votre mot de passe hashé complet.
- Votre identifiant, email, ou toute autre donnée personnelle.

**Comment ça marche (k-Anonymity) :**
L'API reçoit les 5 premiers caractères et renvoie tous les hashs qui commencent par ces caractères. Votre application compare ensuite localement le reste du hash. **L'API ne sait jamais quel mot de passe vous avez cherché.** Votre anonymat est totalement préservé.

---

## Installation

1.  Rendez-vous dans la section **Releases** (à droite sur GitHub).
2.  Téléchargez la dernière version de **`Deep-Pass.exe`**.
3.  Placez le fichier où vous le souhaitez (sur votre Bureau, par exemple).
4.  Double-cliquez pour lancer l'application. Aucune installation n'est nécessaire.

---

## Transférer votre coffre sur mobile (Android) --> **"App en Création..."**

Vous pouvez exporter votre coffre-fort complet pour le transférer sur votre téléphone Android :

1.  Dans Deep-Pass (PC), allez dans **Fichier > Exporter en .vaultpack**.
2.  Un fichier `DeepPass_AAAA-MM-JJ.vaultpack` est créé (c'est une archive ZIP qui contient `vault.db`, `config.json` et un fichier LISEZ-MOI).
3.  Transférez ce fichier sur votre téléphone via un câble USB (jamais par email ou cloud public).
4.  Sur l'application Android, utilisez "Importer un .vaultpack" et saisissez votre mot de passe maître.

**⚠️ Important** : Le fichier `.vaultpack` contient `vault.db` (chiffré) + `config.json` (sel + hash). Il est **totalement inutilisable sans votre mot de passe maître**. Argon2id rend le brute-force quasi impossible. Mais ne le partagez jamais.

---

## Importer un `.vaultpack` sur PC

Si vous avez un coffre-fort créé sur Android (ou une ancienne sauvegarde `.vaultpack`), vous pouvez le rapatrier sur votre PC :

1.  Dans Deep-Pass (PC), allez dans **Fichier > Importer un .vaultpack...**.
2.  Sélectionnez votre fichier `.vaultpack`.
3.  **⚠️ ATTENTION** : L'import **remplace** votre coffre-fort actuel. Tous vos comptes actuels seront écrasés.
4.  Confirmez l'importation.
5.  L'application se ferme automatiquement.
6.  Relancez Deep-Pass et connectez-vous avec le **mot de passe maître du fichier importé**.

**Note** : Cette fonction est utile pour récupérer un coffre depuis Android, restaurer une sauvegarde, ou changer de mot de passe maître (via un `.vaultpack` modifié).

---

## ⚠️ Avertissement important pour vos données

Vos données sont précieusement conservées dans votre dossier utilisateur Windows :
`%APPDATA%\Deep-Pass\vault.db`

**Pensez à sauvegarder régulièrement ce fichier `vault.db`** (sur une clé USB, un disque dur externe, ou dans un cloud sécurisé). En cas de plantage de votre PC, ce fichier est votre seul moyen de retrouver vos mots de passe.

<img width="1917" height="1027" alt="Screenshot-1-Deep-Pass" src="https://github.com/user-attachments/assets/b53c295a-c5dc-48e2-91a5-dd3410b6b22f" />
<img width="1919" height="1031" alt="Screenshot-2-Deep-Pass" src="https://github.com/user-attachments/assets/e7fd9873-4652-48dc-9fdb-f61c7ae4096a" />
<img width="1917" height="1032" alt="Screenshot-3-Deep-Pass" src="https://github.com/user-attachments/assets/fbf11bb6-726f-4c22-a7a1-74ae3b3ffb1d" />
<img width="1918" height="1030" alt="Screenshot-4-Deep-Pass" src="https://github.com/user-attachments/assets/f35a53ca-c534-45f9-bc50-7df7ecfa8e43" />


By Seven & Vous...