# Quickstart

:::{important} Disclaimer
**Le tutoriel est en cours de construction !**
:::

## Git et GitLab

[Git](https://fr.wikipedia.org/wiki/Git) est un outil de [gestion des versions](https://fr.wikipedia.org/wiki/Gestion_de_versions). Il est déjà installé sur les machines du département. Si vous travaillez sur votre machine personnelle, vous pouvez l'[installer vous-même](https://git-scm.com/book/en/v2/Getting-Started-Installing-Git) gratuitement.

[GitLab](https://fr.wikipedia.org/wiki/GitLab) est une plateforme qui permet de stocker vos projets et de diffuser ce travail à tous vos postes (machine de l'IUT, machine personnelle) ainsi qu'à vos collaborateurs.

### Activation de votre compte GitLab

En tant qu'étudiant de l'IUT d'Orsay, vous avez déjà un compte sur le [GitLab de l'IUT](https://git.iut-orsay.fr/).

```{image} ../images/git-iut-orsay.jpg
:alt: git.iut-orsay.fr
:align: center
```

Pour vous authentifier, utilisez vos login et mot de passe du département.

### Personal Access Token

Pour établir une connection sécurisée entre votre machine et le serveur GitLab de l'IUT, nous allons utiliser un **Personal Access Token** (PAT).

Pour créer un PAT :
1. Aller dans votre profile en cliquant sur votre avatar (en haut à gauche) puis **Edit profile**[^edit_profile].
2. Choisir **Access Tokens**[^access_token_menu] dans la barre à gauche.
3. Ajouter un token en cliquant sur **Add new token**[^add_new_token].
4. Ajouter un nom et une date d'expiration d'un an (le maximum possible) après la date d'aujourd'hui.
5. Choisir tous les [scopes](https://docs.gitlab.com/ee/user/profile/personal_access_tokens.html#personal-access-token-scopes).
6. Cliquer sur **Create personal access token**.

:::{important} **SAUVEGARDER VOTRE PAT !!!**
Une fois que vous quittez la page de création, le PAT ne vous sera jamais rappelé. Vous allez devoir utiliser le PAT pour accéder à vos projets !
:::

Vous pouvez créer autant de PAT que vous voulez (une par machine par exemple).

[^edit_profile]: ![Edit Profile](../images/edit-profile.png)

[^access_token_menu]: ![Access Token Menu](../images/access-token-menu.png)

[^add_new_token]: ![Add New Token](../images/add-new-token.png)

### Création d'un projet

Créer votre projet/dépôt (*repository*)[^create_new_project] en cliquant sur `+` en haut à gauche.

[^create_new_project]: ![Create New Project](../images/create-new-project.png)

Créer un projet vide pour tester les fonctionnalités de Git.

:::{important} MonProjet
Dans la suite, nous allons appeler ce projet **MonProjet**. Il ne faut pas oublier de le remplacer avec le nom que vous avez choisi.
:::

Choisir le niveau de visibilité privé pour votre projet et l'option d'initialiser le projet avec un README.

:::{note} README.md
:class: dropdown
Avoir un README en [Markdown](https://fr.wikipedia.org/wiki/Markdown) dans un projet est une pratique standard. Ce README sert comme une description du projet.  
:::

:::{important} Linux
Ce qui suit est fait pour Linux. Il faut adapter les commandes Unix pour Mac OS. Pour Windows, vous pouvez installer l'émulateur [Git for Windows](https://gitforwindows.org/) qui simule Git comme si vous étiez sous Linux (ou d'autres outils similaires).

Si vous n'êtes pas à l'aise avec les commandes depuis le terminal sur Linux, n'oubliez pas que vous pouvez toujours utiliser un gestionnaire de fichier et votre souris comme sur Windows.
:::

### Configurer votre poste de travail local

Vous avez maintenant créer votre projet sur le dépôt distant sur le serveur de l'IUT. Maintenant, pour travailler sur ce projet sur votre machine (localement), il faut d'abord le configurer.

```{code} sh
git config --global user.name "Prénom Nom"
git config --global user.email "prenom.nom@universite-paris-saclay.fr"
```

Maintenant, vous pouver clôner votre dépôt distant pour le télécharger vers votre poste local :
- Cliquer sur le bouton **Code**[^code_button] à droite.
- Copier le code de l'option **Clone with HTTPS**[^clone_https].
- Ouvrir un terminal dans votre répertoire de travail.
- Taper la commande suivante en collant l'adresse que vous aviez copié et en rajoutant votre login et PAT au bon endroit.

```{code} sh
git clone https://<login>:<Personal Access Token>@git.iut-orsay.fr/<login>/monprojet.git
```
[^code_button]: ![Code Button](../images/code-button.png)

[^clone_https]: ![Clone HTTPS](../images/clone-https.png)

Par exemple :
```{code} sh
git clone https://myLogin:1234thisIsYourPAT5678@git.iut-orsay.fr/myLogin/monprojet.git
```

:::{important} Personal Access Token
Il faut ajouter le token que vous avez sauvegardé en haut ! 
- **Pas le nom que vous lui avez donné !**
- **Pas votre mot de passe !**
- **Pas le Feed Token !** (que vous pouvez aussi trouver dans la page Access Token)

Si vous n'avez pas sauvegardé votre PAT, enlever (*Revoke*) celui que vous avez déjà créé et refaire la manipulation.
:::

### Utiliser un IDE : VSCode

Le tutoriel qui suit est fait pour VSCode.

:::{seealso} Sur votre machine personnelle.
:class: dropdown
Si vous travaillez sur votre machine personnelle, vous pouvez aller sur [le site de VSCode](https://code.visualstudio.com/download) pour l'installer.
:::

Ouvrir **VSCode > File > Open Folder...** Ouvrir le dossier contenant votre projet. Sur l'écran vous devez avoir l'*Editor* et tout à gauche, une barre verticale avec *Explorer*, *Search*, *Source Control*, *Run and Debug* et *Extensions*.
- **Editor** est un éditeur de texte de base avec de la coloration syntaxique. 
- **Explorer** est un outil de navigation à l'intérieur de votre projet. 
- **Search** est un outil de recherche à l'intérieur de votre projet.
- **Source Control** est l'intégration Git dans VSCodium. Dans la barre horizontale tout en bas de l'écran, vous avez aussi une barre de statut du projet. Il faut toujours commencer par cliquer sur **Synchronize Changes** à côté de **main** quand vous commencer à travailler. 
    - Maintenant, pour voir comment utiliser *Source Control*, **créer un dossier `Test`** (en utilisant l'interface de l'IDE). À l'intérieur du dossier, **créer un fichier `hello-world.txt`** avec une ligne `Hello World!`.
    - Vous devez voir `1` apparaitre sur l'icône de *Source Control*. Si vous le survolez, c'est marqué *1 pending change(s)*. Il s'agit des changements qui ne sont pas encore *commité* ("approuvé").
    - Dans *Explorer*, vous voyez aussi un point vert à côté du dossier `Test` qui contient le nouveau fichier et à côté du fichier vous voyez un `U` qui est une abbréviation de **Untracked**. Cela indique que ce nouveau fichier n'a pas encore été suivi. 
    - Si vous modifiez un fichier existant, vous devez voir la lettre `M` en jaune qui est court pour **Modified** et qui indique aussi que cette modification n'a pas été suivie.
    - Cliquer sur *Source Control*. Vous devez voir les nouveaux changements du projet. Vous pouvez suivre le nouveau fichier `hello-world.txt` en cliquant sur le `+` qui indique **Stage Changes**. Il y a deux catégories de changements qui apparaissent : **Staged Changes** et **Changes**. *Staged Changes* correspond aux changements qui sont suivis. Maintenant, dans *Explorer* vous devez voir la lettre `A` apparaitre à côté de `hello-world.txt` qui est une abbréviation de **Added** ("suivi").
    - Écrire un message de commit dans la barre **Message**. Cliquer sur **Commit**. Vous voyez apparaitre **Outgoing** et la branche **main**, ce qui indique que ces changements vont être effectués sur la branche *main* (espace ).
    - Vous pouvez maintenant cliquer sur **Sync Changes** qui va synchroniser votre dépôt local avec le dépôt distant.
- **Run and Debug** sert à débugger votre code (ne pas l'utiliser si vous ne savez pas comment l'utiliser).
- **Extensions** permet d'ajouter des extensions qui rajoutent des fonctionnalités à notre IDE.

### .gitignore

À cause des fichiers de configurations et des fichiers générés lors de la compilation, notre projet est pollué avec des fichiers non voulus.


### Synchronisation du dépôt local avec le dépôt distant


### Création du projet d'équipe

Ajouter les membres de votre équipe :
- Cliquer sur **Manage** à gauche puis **Members**[^manage_members].
- Cliquer sur **Invite members** en haut à droite.
- Ajouter les membres de votre équipe avec le rôle **Maintainer** (qui lui donne presque autant de droit sur le projet que vous l'**Owner**).

[^manage_members]: ![Manage Members](../images/manage-members.png)

## Résolution des conflits

:::{important} Disclaimer
:class: dropdown
La résolution de conflits que nous allons voir est une résolution simple quand vous avez qu'une seule branche de travail.
:::

Parfois, on oublie de faire un pull (récupération des fichiers du dépôt distant --- commun avec les autres membres de l'équipe) avant de commencer à travailler et on modifie un fichier qui n'est plus à jour. Lors du push (synchronisation du dépôt local et du dépôt distant) des nouvelles modifications, Git nous informe que les fichiers sont différents et c'est à nous de décider comment fusionner les deux versions. Cela pourrait arriver aussi quand plusieurs personnes travaillent sur le même fichier et les modifications faites rentrent en conflit. Aujourd'hui, nous allons apprendre à gérer ces conflits.

Pour commencer, créer un dossier `Test` et un fichier `conflict.md` avec le contenu suivant.

```{code} md
# Conflict resolution in Git

Let's learn some conflict resolution in Git.

## Merge without conflicts

Write something here on GitLab Web IDE:

Write something else here locally without pulling from GitLab first: 

## Merge with conflicts

Write something here on GitLab Web IDE and something else locally without pulling from GitLab first:
```

Synchroniser votre dépôt local avec le dépôt distant.

### Merge Simple

Nous allons commencer par un exemple où le même fichier a reçu des modifications différentes mais ces modifications peuvent être fusionnées sans conflits.

Ouvrir le Web IDE de GitLab et ajouter du texte. Par exemple,
```{code} md
Write something here on GitLab Web IDE: Hello
```

Commit vos modifications pour avoir cette nouvelle version de `conflict.md` sur GitLab.

Sans récupérer ces nouvelles modifications sur votre dépôt local, ajouter du texte dans `conflict.md` sur votre poste de travail. Par exemple,
```{code} md
Write something else here locally without pulling from GitLab first: Hi
```

Synchroniser vos changements locaux avec le dépôt distant.

Vous allez recevoir un message d'erreur avec comme option `Show Command Output`. Cliquer dessus.

Il vous indique qu'il y a des branches divergentes dans votre dépôt, ce qui signifie qu'il y a plusieurs versions différentes d'un même fichier et que nous allons devoir les fusionner.

Appuyer sur `F1` pour ouvrir la barre de commande dans VSCodium. Dans la barre de commande, taper `git merge` puis cliquer sur l'option `Git: Merge` qui vous est proposé.

Maintenant, il vous propose plusieurs branches et il faut choisir avec quelle branche on va fusionner. Choisir `origin/HEAD` (qui représente la branche courante sur le dépôt distant).

La fusion a fonctionné, maintenant vous devez voir sur votre poste de travail les deux modifications.
```{code} md
Write something here on GitLab Web IDE: Hello

Write something else here locally without pulling from GitLab first: Hi
```

Il est prêt pour synchroniser les deux dépôts et les deux contiennent la même version du fichier.

### Merge avec conflits

Dans l'exemple précécent, nous avons vu une fusion où les modifications sur les deux versions différentes du même fichier ne rentrent pas en conflit et la fusion pouvait se faire automatiquement.

Cette fois, on va refaire la même manipulation sauf que sur le Web IDE de GitLab, on va écrire par exemple,
```{code} md
Write something here on GitLab Web IDE and something else locally without pulling from GitLab first: Hello
```
alors que localement on va écrire
```{code} md
Write something here on GitLab Web IDE and something else locally without pulling from GitLab first: Hi
```

En refaisant `git merge` (à travers la barre de commande avec `F1`) avec la branche `origin/HEAD`, l'IDE nous montre le fichier `conflict.md` avec les deux versions différentes.
```{figure} ../images/merge-conflict.png
:alt: Merge conflict
:align: center
```

`HEAD` correspond à la version courante sur le dépôt local et `origin/HEAD` correspond à la version courante sur le dépôt distant.
- `Accept Current Change` va garder la version de `HEAD`.
- `Accept Incoming Change` va garder la version de `origin/HEAD`.
- `Accept Both Changes` va concaténer les deux versions.
- `Compare Changes` va ouvrir les deux versions dans deux tabs différents.

La meilleure solution est d'appuyer sur le bouton `Resolve in Merge Editor` qui apparaît en bas à droite.

Ce bouton va ouvrir trois fenêtres `Current`, `Incoming` et `Result` qui correspondent respectivement à la version de `HEAD`, la version de `origin/HEAD` et la version finale que l'on veut.

Dans ce cas, peut-être que l'on a envie de faire une version fusionnée complètement différente des deux versions proposées.

Écrire `Haha` au lieu de `Hello` et `Hi` dans `Result` puis appuyer sur `Complete Merge`.

Maintenant, vous pouvons synchroniser les deux dépôts avec cette version finale de `conflict.md`. 

## Unity

- **Installer Unity** : Vous pouvez installer Unity sur votre machine personnelle ou utiliser la version des machines l'IUT.
- **Créer un compte Unity**.
- **IDE** : [VSCode](https://learn.unity.com/tutorial/get-started-with-scripts?uv=2021.3).

:::{important} .gitignore
Utiliser ce [`.gitignore`](https://github.com/github/gitignore/blob/main/Unity.gitignore) et y rajouter `.vscode/` si vous êtes sur VSCode.
:::

:::{seealso} Extensions VSCode
Si vous utilisez VSCode, vous pouvez aussi installer `Unity Code Snippets` et des extensions pour C#. 
:::

:::{important} Unity Learn
Unity a beaucoup de tutoriels sur Unity Learn pour apprendre à utiliser Unity.
:::

## Godot