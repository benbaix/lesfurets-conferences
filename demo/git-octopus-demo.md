# git-octopus demo

```bash
    # Nous avons deux depôts de code, soit studies et features
    git branch -a | grep studies
    git branch -a | grep features

    # Vérifier l'installation de git octopus
    git help octopus

    # Executer git-octopus sur une branche qui n'est pas en conflit
    git checkout AMX-12345_branche_sans_conflit
    git octopus
    git octopus features/*
    git reset --hard HEAD~1
    git octopus -n features/*

    # Executer git-octopus sur une branche qui a un conflit
    git checkout AMX-12345_branche_avec_conflit
    git octopus -n features/*

    # Résoudre le conflit avec git-conflict
    git conflict refs/remotes/features/AMX-11369_Funnel_Modification_du_type_des_champs
    git mergetool
    git conflict --continue

    # Exécuter git-octopus pour vérifier l'application de la résolution
    # puis pousser la résolution
    git push features refs/conflicts/???
    git octopus -n features/*
    git push --delete features refs/conflicts/???

    # Maintenant l'UL et tout les utilisateurs de votre repo ont accès à la
    # résolution, la configuration de fetch est légèrement différente
    vim .git/config

    # Configurer git-octopus pour éviter les arguments
    git config octopus.commit false
    git config octopus.pattern "remotes/features/*"
    git octopus
```
