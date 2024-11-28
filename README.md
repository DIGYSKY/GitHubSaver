# GitHubSaver - Gestionnaire de sauvegarde GitHub

Un script Bash pour sauvegarder et synchroniser automatiquement tous vos dépôts GitHub.

## 📋 Prérequis

- Git installé sur votre système
- Un token GitHub avec les permissions appropriées
- jq (JSON processor) installé sur votre système
- Bash shell

## 🚀 Installation

1. Téléchargez le script `githubsaver`
2. Rendez-le exécutable :
```bash
chmod +x githubsaver
```

**Note :** il se peut qu'un décalage se produise entre le moment ou vous ajouter à votre GitHub un nouveau dépôt et le moment ou le script le détecte. Ce décalage est du à la synchronisation des données entre GitHub et l'API GitHub.

3. Configurez votre token GitHub :
### Initialisation du token GitHub

Pour utiliser ce script, vous devez créer un token GitHub avec les permissions appropriées et l'enregistrer sur votre système. Suivez les étapes ci-dessous pour initialiser le token :

1. Connectez-vous à votre compte GitHub.
2. Accédez à la section des paramètres de votre compte en cliquant sur votre avatar en haut à droite, puis sur "Settings".
3. Dans le menu de gauche, cliquez sur "Developer settings".
4. Cliquez sur "Personal access tokens", puis sur "Generate new token".
5. Donnez un nom à votre token, par exemple "Save Script Token".
6. Sélectionnez les permissions nécessaires pour le token. Pour ce script, vous aurez besoin des permissions suivantes :
   - `repo` (accès complet aux dépôts privés et publics)
7. Cliquez sur "Generate token" en bas de la page.
8. Copiez le token généré et enregistrez-le dans un endroit sûr. **Notez que vous ne pourrez plus voir ce token après avoir quitté cette page.**

Ensuite, enregistrez le token dans le script en utilisant la commande suivante :

```bash
./githubsaver --set-token <votre_token_github>
```

## 💻 Utilisation

### Commandes disponibles

```bash
./githubsaver [OPTIONS]
```

### Options

- `--all, -a` : Met à jour tous les dépôts et leurs branches
- `--master` : Met à jour uniquement la branche par défaut de tous les dépôts
- `--set-token <token>` : Enregistre un nouveau token GitHub
- `--show-token` : Affiche le token GitHub actuel
- `--last-save` : Affiche les informations de la dernière sauvegarde
- `--show-save` : Affiche une liste des sauvegardes disponibles
- `--help, -h` : Affiche l'aide

### Exemples d'utilisation

1. Sauvegarder tous les dépôts avec toutes les branches :
```bash
./githubsaver --all
```

2. Mettre à jour uniquement les branches principales :
```bash
./githubsaver --master
```

3. Voir la dernière sauvegarde :
```bash
./githubsaver --last-save
```

### Arborescence des dossiers

```
README.md
.gitignore
.token
githubsaver
save_repos/
    save_YYYYMMDD_HHMMSS.log
    nom_du_dossier_du_repo_1/
    nom_du_dossier_du_repo_2/
    ...
```

## 📊 Fonctionnalités

- Barre de progression en temps réel
- Journalisation détaillée des opérations
- Gestion de toutes les branches des dépôts
- Estimation du temps restant
- Historique des sauvegardes
- Gestion sécurisée du token GitHub

## 📝 Logs

Les logs sont automatiquement générés dans des fichiers au format :
```
save_YYYYMMDD_HHMMSS.log
```

## ⚠️ Notes importantes

1. Assurez-vous d'avoir suffisamment d'espace disque pour cloner tous vos dépôts
2. Le token GitHub doit avoir les permissions nécessaires pour accéder à vos dépôts
3. La première exécution peut prendre plus de temps car elle clone tous les dépôts

## 🔒 Sécurité

- Le token GitHub est stocké localement dans un fichier `.token`
- Ne partagez jamais votre token GitHub
- Utilisez des permissions minimales pour votre token

## 🐛 Dépannage

Si vous rencontrez des erreurs :
1. Vérifiez que votre token est valide
2. Assurez-vous d'avoir une connexion Internet stable
3. Vérifiez les logs pour plus de détails sur les erreurs

