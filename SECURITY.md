# Politique de Sécurité

## Signaler une vulnérabilité
La sécurité de Deep-Pass est une priorité. Si vous découvrez une faille de sécurité, merci de **ne pas** créer une "Issue" publique. 
Veuillez me contacter directement par message privé sur GitHub ou via mon profil : [@Septieme7](https://github.com/Septieme7).

Je m'engage à analyser toute faille signalée et à publier un correctif dans les plus brefs délais.

## Architecture de sécurité
- Vos données sont chiffrées en AES-256-GCM.
- Votre mot de passe maître est haché avec Argon2id.
- Deep-Pass fonctionne 100% hors-ligne (aucune donnée n'est envoyée sur Internet, sauf si vous lancez manuellement le scanner de fuites).