# Racines : tout pour le Play Store

Adresse de l'appli : https://toinou08.github.io/racines/
Politique de confidentialité : https://toinou08.github.io/racines/privacy.html
E-mail de contact : roadt0654@gmail.com

---

## 1. Les textes de la fiche (à copier-coller dans la Play Console)

**Nom de l'appli** (30 caractères max)
> Racines : arrêter le porno

**Description courte** (80 caractères max)
> Arrête le porno en faisant pousser ton arbre : séries, défis et bouton SOS.

**Description complète**
> Tu veux arrêter le porno ? Racines t'aide à reprendre le contrôle, un jour à la fois, sans jugement.
>
> 🌳 TON ARBRE POUSSE AVEC TOI
> Chaque jour sans porno, ton arbre grandit. Tu gagnes de l'XP, tu passes des niveaux (de la graine à la forêt) et tu vois ta série de jours avancer vers ton objectif : une semaine, un mois ou 90 jours.
>
> 🆘 UN BOUTON SOS QUAND L'ENVIE ARRIVE
> Une envie, c'est une vague : elle monte, puis elle redescend. Appuie sur SOS : 90 secondes de respiration guidée, tes propres raisons d'arrêter et des conseils adaptés aux moments où tu es le plus fragile.
>
> ✅ DES DÉFIS CHAQUE JOUR
> Pompes, marche, appel à un ami, téléphone hors de la chambre… Six nouveaux défis chaque jour pour remplacer l'habitude par du concret.
>
> 🏅 DES BADGES À DÉBLOQUER
> Premier jour, une semaine, un mois, 90 jours, 10 envies vaincues… Chaque étape compte.
>
> 💬 UNE PENSÉE PAR JOUR
> Sénèque, Marc Aurèle, Épictète, Montaigne : une phrase chaque jour pour tenir bon.
>
> 🔁 SI TU CRAQUES
> Ça arrive. Ta série repart à zéro, mais tu gardes ton XP, tes badges et ton record. Tu peux noter ce qui a déclenché la rechute pour repérer ce qui revient.
>
> 🌙 UN RAPPEL CHAQUE SOIR
> Ajoute un rappel discret dans ton agenda pour faire le point chaque soir.
>
> 🔒 TOTALEMENT PRIVÉ
> Pas de compte, pas de pub, rien n'est envoyé : tout reste sur ton téléphone. Code de verrouillage, mode discret et floutage de l'écran disponibles.

**Catégorie** : Santé et remise en forme
**Tags** : bien-être, habitudes, santé mentale (choisis ceux que la Console propose)

---

## 2. Les images (dans le dossier `store`)

- **Icône 512 × 512** : `icons/icon-512.png`
- **Image de présentation 1024 × 500** : `store/image-presentation-1024x500.png`
- **Captures téléphone** (au moins 2, ici 5) : `store/captures/capture-1.png` à `capture-5.png`

---

## 3. Créer le fichier Android avec PWABuilder

1. Va sur **pwabuilder.com**.
2. Colle l'adresse `https://toinou08.github.io/racines/` puis clique sur **Start**.
3. Clique sur **Package for stores**, puis sur **Generate Package** dans la case **Android**.
4. Vérifie ces réglages :
   - **Package ID** : `io.github.toinou08.racines` ⚠️ il ne pourra plus jamais changer.
   - **App name** : Racines. **Version** : 1.0.0. **Version code** : 1.
   - **Signing key** : laisse **Create new**.
5. Clique sur **Download**. Tu obtiens un fichier zip. À l'intérieur :
   - `*.aab` : le fichier à envoyer sur le Play Store.
   - `signing.keystore` et `signing-key-info.txt` : ta **clé de signature**. ⚠️ Garde-les précieusement (clé USB + Google Drive privé). **Ne les mets JAMAIS sur GitHub.** Sans elles, tu ne pourras plus mettre l'appli à jour.
   - `assetlinks.json` : sert à cacher la barre d'adresse du navigateur dans l'appli (voir étape 5).

---

## 4. Publier en test fermé sur la Play Console

1. **play.google.com/console** → **Créer une application**.
   Nom : Racines · Langue : Français · Type : Application · Gratuite. Coche les déclarations.
2. **Configurer l'application** (le tableau de bord liste les tâches). Réponses :
   - **Règles de confidentialité** : `https://toinou08.github.io/racines/privacy.html`
   - **Accès à l'appli** : toutes les fonctionnalités sont accessibles sans restriction.
   - **Annonces** : Non, l'appli ne contient pas d'annonces.
   - **Classification du contenu** : catégorie « Toutes les autres applications ». L'appli parle d'arrêter le porno mais ne montre **aucun** contenu sexuel : réponds Non aux questions sur le contenu sexuel ou la nudité. Pas d'interaction entre utilisateurs, pas d'achats.
   - **Public cible** : **18 ans et plus uniquement**.
   - **Sécurité des données** : « Non, l'appli ne collecte ni ne partage aucune donnée utilisateur ».
   - **Appli gouvernementale / financière / santé** : Non. Si la Console te demande de préciser une fonctionnalité de santé, choisis celle qui correspond le mieux à « bien-être / habitudes » ou « aucune ».
   - **Fiche Play Store** : colle les textes et les images des parties 1 et 2. E-mail : roadt0654@gmail.com
3. Menu **Tester** → **Test fermé** → **Créer un canal** (ou utiliser « Alpha »).
   - **Testeurs** : crée une liste avec les adresses Gmail de **12 personnes minimum** (vise 15 à 20, car certains oublient).
   - **Créer une version** → envoie le fichier `.aab` → Notes de version : « Première version de test ».
   - **Envoyer pour examen**. Google vérifie en quelques jours.
4. Une fois validé, copie le **lien de participation** et envoie-le à tes testeurs. Ils doivent l'ouvrir avec le même compte Gmail, accepter, installer l'appli et **la garder 14 jours d'affilée**.
5. Après 14 jours : **Tableau de bord** → **Demander l'accès à la production**, puis publie pour tout le monde.

---

## 5. Cacher la barre d'adresse (assetlinks)

Sans ce fichier, l'appli fonctionne, mais une barre d'adresse du navigateur s'affiche en haut.
Comme Racines est sur `toinou08.github.io/racines`, le fichier doit être à la **racine** : `https://toinou08.github.io/.well-known/assetlinks.json`.

1. Sur GitHub, crée un nouveau dépôt nommé exactement **`toinou08.github.io`** (public).
2. Ajoute-le dans la conversation avec Claude : il y mettra `assetlinks.json` (et le fichier `.nojekyll` indispensable).
3. Après le premier envoi sur la Play Console, va dans **Intégrité de l'application** → **Signature d'application** et copie l'**empreinte SHA-256**. Elle doit aussi être ajoutée dans `assetlinks.json`, sinon la barre reviendra pour les testeurs.
