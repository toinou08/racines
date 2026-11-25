# Racines

Appli pour arrêter le porno : un arbre qui pousse avec la série de jours, XP, défis du jour, badges, bouton SOS (90 s de respiration), pensée du jour, rappel du soir. Ton complice et chaleureux, jamais moralisateur.

- En ligne (GitHub Pages, branche `main`, dossier racine) : https://toinou08.github.io/racines/
- Destination : Play Store, empaquetée en TWA avec PWABuilder. Package ID prévu : `io.github.toinou08.racines`.
- Contact développeur : roadt0654@gmail.com

## Le propriétaire

Antoine (toinou08) débute en programmation et ne parle pas anglais. Réponds-lui en **français simple**, sans jargon. Traduis les termes anglais de GitHub et des outils quand ils apparaissent. Il préfère voir avant d'adopter : pour un changement visible, fais d'abord une branche de test avec des captures d'écran, puis fusionne dans `main` quand il valide.

## Structure

Pas de build, pas de dépendances : du HTML, du CSS et du JS purs.

- `index.html` : toute l'appli (CSS, balisage, script) dans un seul fichier.
- `sw.js` : service worker (réseau d'abord, cache hors ligne).
- `manifest.webmanifest` : manifeste PWA (icônes, captures, raccourci SOS `?sos=1`).
- `privacy.html` : politique de confidentialité, liée depuis le Play Store.
- `icons/` : icônes (192, 512, maskable, apple-touch).
- `screenshots/` : captures 1080×1920 référencées par le manifeste.
- `store/` : fiche Play Store (`FICHE-PLAY-STORE.md`), captures avec légendes, image de présentation 1024×500.

## Règles à respecter

- **Ne jamais casser les données des utilisateurs.** Tout est dans `localStorage` sous la clé `racines-v1` (thème : `racines-theme`). Ne renomme pas la clé. Ajoute les nouveaux champs avec une valeur par défaut (`Object.assign(fresh(), …)`).
- **À chaque modification d'un fichier mis en cache**, incrémente `CACHE` dans `sw.js` (`racines-vN`) pour que les téléphones récupèrent la nouvelle version.
- **Confidentialité** : rien n'est envoyé à un serveur, pas de compte, pas de pub, pas de suivi. Si une fonctionnalité stocke une nouvelle donnée ou contacte un service, mets `privacy.html` à jour (et la date), ainsi que la section « Sécurité des données » de `store/FICHE-PLAY-STORE.md`.
- **Mode discret** : tout texte affiché qui contient « porno » doit passer par `DSC()`. Les textes visibles hors de l'appli (agenda, notifications) restent neutres (« Racines »).
- **Respecte les réglages existants** : code de verrouillage, floutage, « Garder mes notes » (si désactivé, ne rien enregistrer de nouveau en texte libre), « Tout effacer ».
- **Accessibilité** : boutons d'au moins 44 px, `prefers-reduced-motion` respecté, thèmes clair et sombre (`light-dark()`).
- Tout le texte de l'interface est en français.
- **Ne jamais mettre sur GitHub** la clé de signature Android (`*.keystore`, `*.jks`, `signing-key-info.txt`) : le dépôt est public.

## Vérifier avant de pousser

1. Vérifier la syntaxe du script : `node -e "const s=require('fs').readFileSync('index.html','utf8');s.split('<script>').slice(1).forEach(p=>new Function(p.split('</script>')[0]))"`
2. Servir le dossier (`python3 -m http.server 8765`) et passer chaque onglet dans un navigateur sans interface (Playwright + `/usr/bin/google-chrome`), en clair et en sombre, en écran 390×844. Aucune erreur dans la console. Regarder les captures.
3. Commits en français. Pousser une branche de test, puis `main` quand Antoine valide.
