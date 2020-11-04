# <p style="color: #0066ff;">Aide-mémoire git</p>

Presque tout peut se faire à partir du terminal de VS Code.

### <p style="color: #0066ff;">1. Clone</p>
Commencer par cloner le travail qui est sur GitHub dans notre ordi à l'endroit qu'on le veut. On le fait seulement une fois.

    git clone https://github.com/repo_owner_username/repo_name.git

Pour les fois suivantes, on commence à partir de l'étape 2.

### <p style="color: #0066ff;">2. Aller dans branche_main_locale</p>
On s'assure qu'on est dans la branche main_locale avant de poursuivre. Sinon on fout la marde.

    git checkout main

### <p style="color: #0066ff;">3. Importer les changements de branche_main_remote</p>
On s'assure que notre branche main_locale est pareille à notre branche main_remote avant de faire des modifs. Donc on importe la branche main_remote, et s'il y a eu des changements, notre branche main_locale va maintenant les avoir.

    git pull

S'il n'y a pas eu de changement, il va être écrit "Already up to date."

### <p style="color: #0066ff;">4. Créer et changer de branche en même temps</p>
On crée ensuite une branche pour pouvoir modifier le travail sans que ça foute la marde quand on va vouloir merge, dans le cas où un de nous a fait des modifs sur main_remote. Donc on crée une "copie" de la branche main_locale dans une autre branche locale. C'est celle-là qu'on va modifier.

    git checkout -b branche_a_modifier_locale

Ou sinon:

#### <p style="color: #00ff08;">4.1 Pour créer une branche</p>

    git branch branche_a_modifier_locale

#### <p style="color: #00ff08;">4.2 Pour changer de branche</p>

    git checkout branche_a_modifier_locale


##### On fait les modifications qu'on veut dans notre éditeur (VS Code)
    
### <p style="color: #0066ff;">5. Ajouter les changements dans un futur commit</p>
Toujours à partir de notre branche secondaire (pour modif), on ajoute les changements dans une "liste d'attente" en vue d'un futur commit (*staging*).

Pour ajouter un fichier:

    git add fichier_modifiee.extension

Pour ajouter tout au complet:

    git add .
    
### <p style="color: #0066ff;">6. Faire un commit</p>
On fait le commit, les changements qui sont en staging s'ajoutent automatiquement au commit.

On ajoute un court message pour dire en gros qu'est-ce qu'on a fait.

    git commit -m "Message pertinant sur les modifications"

### <p style="color: #0066ff;">7. Pull la main_remote dans branche_modifiee_locale</p>
Avant de mettre nos changements sur GitHub, on s'assure d'avoir la version la plus à jour de main_remote. Donc on prend le main_remote et on le pull dans branche_modifiee_locale.

    git pull origin main
    
### <p style="color: #0066ff;">8. Envoyer les commits vers GitHub</p>
On prend notre branche_modifiee_locale, et on fait comme si on créait la même branche en remote. Donc après on est censé avoir main_remote (non modifiée), branche_modifiee_remote (avec modifs), main_locale (non modifiée), branche_modifiee_locale (avec modifs).

    git push origin branche_modifiee

### <p style="color: #0066ff;">9. Créer une Pull Request</p>
On va sur le site de GitHub dans le repo. Il devrait être écrit qu'il y a eu des commits. On clique sur "Compare & pull request". Maintenant branche_modifiee_remote est comparée à main_remote. En faisant ça, GitHub s'assure que les deux branches sont compatibles. Elles devraient l'être puisqu'on a pull juste avant. S'il est écrit "Able to merge", on peut alors cliquer sur "Create Pull Request".

### <p style="color: #0066ff;">10. Merge</p>
 La branche est encore comparée à la main, et là il devrait être écrit "This branch has no conflicts with the base branch". Il reste seulement à cliquer sur "Merge pull request" et "Confirm merge". On peut laisser notre teammate Merge, ça lui permet de voir les changements qui ont été faits.

### <p style="color: #0066ff;">11. Suppression de branche_modifiee_remote</p>
Une fois que le merge a été fait, GitHub "supprime" la branche_modifiee_remote (en fait elle est encore là mais on la voit pas). Cependant, elle est encore présente localement. C'est pour ça que la prochaine fois qu'on veut faire des modifications, il faut s'assurer de retourner à l'étape 2 et aller dans la branche main_locale (checkout) à partir de notre ternimal. Sinon ça fout la marde quand on pull.

### <p style="color: #ff00bf;">On est rendu où? </p>
En tout temps, on peut regarder le statut du document/de la branche. Ça permet aussi de voir si le fichier a été ajouté, modifié, supprimé, ou si celui-ci est en staging. On va dans la branche_locale qu'on veut avoir le statut (checkout) et on fait la demande.

    git status

### <p style="color: #ff00bf;">Voir les différences entre les modifs</p>
On peut regarder les différences entre notre main_locale (donc avant modifications) et notre branche_modifiee_locale (avec modifications).

    git diff

### <p style="color: #ff00bf;">Voir les derniers commits effectués</p>
On peut voir les derniers commits qui ont été faits dans le repo. 

    git log

