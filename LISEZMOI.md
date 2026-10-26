# Stock Anapath

Application de gestion du stock du service (anticorps d'IHC, produits chimiques, fongibles).
Elle fonctionne sur PC et sur téléphone, avec les mêmes données partagées en ligne (Supabase),
et s'installe comme une application.

## 1. Créer la base de données (Supabase, gratuit)

1. Créez un compte sur https://supabase.com, puis **New project** (région : Europe).
2. Menu **SQL Editor** > **New query** : copiez tout le contenu de `supabase.sql`, puis cliquez sur **Run**.
   Cela crée la table, les règles d'accès et les 224 articles du catalogue.
3. Menu **Authentication** > **Sign In / Providers** : désactivez **Allow new users to sign up**.
   Ainsi, personne ne peut se créer un compte tout seul.
4. Menu **Authentication** > **Users** > **Add user** > **Create new user** :
   saisissez l'e-mail et un mot de passe pour chaque personne autorisée (cochez **Auto Confirm User**).
5. Menu **Project Settings** > **API** : copiez **Project URL** et la clé **anon public**.

## 2. Relier l'application à la base

Ouvrez `config.js` et collez les deux valeurs :

```js
window.SUPA_URL = "https://xxxxxxxx.supabase.co";
window.SUPA_KEY = "eyJhbGciOi...";
```

La clé « anon public » peut être publiée : sans compte valide, elle ne donne accès à aucune donnée.

## 3. Mettre en ligne sur GitHub Pages

1. Créez un dépôt (par exemple `stock-anapath`) et envoyez-y **tous les fichiers de ce dossier**.
2. **Settings** > **Pages** > Source : **Deploy from a branch**, branche `main`, dossier `/ (root)`.
3. Après une minute, l'adresse est : `https://<votre-compte>.github.io/stock-anapath/`

## 4. Installer sur le PC et le téléphone

- **PC (Chrome ou Edge)** : ouvrez l'adresse, puis cliquez sur l'icône **Installer** à droite de la barre d'adresse.
- **Android (Chrome)** : menu ⋮ > **Installer l'application** (ou **Ajouter à l'écran d'accueil**).
- **iPhone (Safari)** : bouton Partager > **Sur l'écran d'accueil**.

Chaque personne se connecte avec l'e-mail et le mot de passe créés à l'étape 1.4.

## Bon à savoir

- Une connexion internet est nécessaire pour lire et enregistrer les données.
- Ce qui est saisi sur un appareil apparaît sur les autres en direct.
- Le menu **Données** > **Sauvegarde complète (.json)** reste disponible pour garder une copie.
- Pour retirer l'accès à quelqu'un : Supabase > Authentication > Users > supprimer l'utilisateur.
- Le plan gratuit de Supabase met en pause un projet resté 7 jours sans aucune activité.
  Il suffit de le réactiver depuis le tableau de bord Supabase (les données sont conservées).
