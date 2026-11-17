# Politique de Sécurité

## Signaler une vulnérabilité

La sécurité de Deep-Pass est une priorité. Si vous découvrez une faille de sécurité, merci de **ne pas** créer une "Issue" publique. 

Veuillez me contacter directement par message privé sur GitHub ou via mon profil : [@Septieme7](https://github.com/Septieme7).

Je m'engage à analyser toute faille signalée et à publier un correctif dans les plus brefs délais.

---

## Architecture de sécurité

- **Chiffrement des données** : AES-256-GCM (Galois/Counter Mode) avec nonce aléatoire de 96 bits.
- **Hachage du mot de passe maître** : Argon2id (recommandé par l'OWASP) avec 64 MiB de mémoire et 3 itérations.
- **Dérivation de clé** : PBKDF2 avec SHA-256 et 200 000 itérations.
- **Stockage** : Base SQLite locale dans `%APPDATA%\Deep-Pass\vault.db`.
- **100% hors-ligne** : Aucune donnée n'est envoyée sur Internet, **sauf si vous lancez manuellement le scanner de fuites (HIBP)**.

---

## Le scanner de fuites (HIBP) : ce qui est envoyé

Deep-Pass utilise l'API **Have I Been Pwned** pour vérifier si vos mots de passe ont fuité. Cette fonction est **manuelle** (vous devez cliquer sur "Vérifier les fuites").

**Ce qui est envoyé à l'API :**
- Uniquement les **5 premiers caractères** du hash SHA-1 de votre mot de passe.

**Ce qui n'est JAMAIS envoyé :**
- Votre mot de passe en clair.
- Votre mot de passe hashé complet.
- Votre identifiant, email, ou toute autre donnée personnelle.
- Votre mot de passe maître.

**Principe de k-Anonymity :**
L'API reçoit les 5 premiers caractères et renvoie tous les hashs correspondants. Votre application compare ensuite localement le reste du hash. **L'API ne sait jamais quel mot de passe vous avez cherché.** Votre anonymat est totalement préservé.

---

## Bonnes pratiques de sécurité

1. **Utilisez un mot de passe maître fort** (16+ caractères, avec majuscules, minuscules, chiffres et symboles).
2. **Ne partagez jamais votre fichier `.vaultpack`** sur Internet (email, cloud public, réseaux sociaux).
3. **Sauvegardez régulièrement votre fichier `vault.db`** sur un support sécurisé (clé USB, disque externe).
4. **Transférez vos fichiers `.vaultpack` uniquement par câble USB** ou cloud privé de confiance.

---

## Versions supportées

Seule la dernière version de Deep-Pass reçoit des correctifs de sécurité.

| Version | Supportée |
| :--- | :---: |
| v7.4.x | ✅ Oui |
| v7.3.x | ✅ Oui |
| v7.2.x | ✅ Oui |
| v7.1.x | ✅ Oui |
| v7.0.x | ❌ Non |
| < v7.0 | ❌ Non |