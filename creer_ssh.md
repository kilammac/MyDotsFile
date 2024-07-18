# Creer une cle SSH pour github
> **ChatGPT** : Configurer une clé SSH pour GitHub sous Arch Linux implique plusieurs étapes. Voici un guide détaillé :
>
> ### Étape 1 : Vérifiez les clés SSH existantes
>
> Ouvrez un terminal et tapez :
>
> ```bash
> ls -al ~/.ssh
> ```
>
> Cela liste les fichiers dans le répertoire `.ssh`. Si vous voyez des fichiers comme `id_rsa` et `id_rsa.pub`, vous avez déjà des clés SSH. Si ce n'est pas le cas, passez à l'étape suivante pour en générer une nouvelle.
>
> ### Étape 2 : Générer une nouvelle clé SSH
>
> Si vous n'avez pas de clé SSH, vous pouvez en générer une en utilisant la commande suivante :
>
> ```bash
> ssh-keygen -t ed25519 -C "votre_email@example.com"
> ```
>
> Si vous utilisez une version de SSH qui ne supporte pas `ed25519`, vous pouvez utiliser `rsa` :
>
> ```bash
> ssh-keygen -t rsa -b 4096 -C "votre_email@example.com"
> ```
>
> Vous serez invité à entrer un nom pour le fichier (vous pouvez appuyer sur `Entrée` pour accepter le nom par défaut) et un mot de passe (optionnel).
>
> ### Étape 3 : Ajouter la clé SSH à l'agent SSH
>
> Démarrez l'agent SSH et ajoutez votre clé :
>
> ```bash
> eval "$(ssh-agent -s)"
> ssh-add ~/.ssh/id_ed25519
> ```
>
> Ou si vous avez généré une clé RSA :
>
> ```bash
> ssh-add ~/.ssh/id_rsa
> ```
>
> ### Étape 4 : Ajouter la clé SSH à votre compte GitHub
>
> 1. Copiez la clé SSH dans votre presse-papiers :
>
>    ```bash
>    cat ~/.ssh/id_ed25519.pub
>    ```
>
>    Ou pour une clé RSA :
>
>    ```bash
>    cat ~/.ssh/id_rsa.pub
>    ```
>
>    Sélectionnez et copiez le contenu de la clé publique.
>
> 2. Allez sur GitHub et connectez-vous à votre compte.
>
> 3. Dans le coin supérieur droit de n'importe quelle page, cliquez sur votre photo de profil, puis sur **Settings**.
>
> 4. Dans la barre latérale des paramètres, cliquez sur **SSH and GPG keys**.
>
> 5. Cliquez sur **New SSH key** ou **Add SSH key**.
>
> 6. Dans le champ "Title", ajoutez un label pour la nouvelle clé. Collez votre clé dans le champ "Key".
>
> 7. Cliquez sur **Add SSH key**. Vous serez peut-être invité à entrer votre mot de passe GitHub pour confirmer.
>
> ### Étape 5 : Testez votre connexion
>
> Pour vérifier que tout fonctionne, utilisez :
>
> ```bash
> ssh -T git@github.com
> ```
>
> Vous devriez voir un message vous accueillant sur GitHub.
>
> Et voilà, vous avez configuré une clé SSH pour GitHub sur votre Arch Linux !
