# Qui a fait une modification

[link to the video](https://openclassrooms.com/fr/courses/2342361-gerez-votre-code-avec-git-et-github/2433716-retrouvez-qui-a-fait-une-modification )

   Pour retrouver qui a modifié une ligne précise de code dans un projet, faire une recherche avec git log peut s'avérer compliqué, surtout si le projet contient beaucoup de commits. Il existe un autre moyen plus direct de retrouver qui a fait une modification particulière dans un fichier : la commande git blame.
```csh
   git blame nomdufichier.extension
```

   Cette commande liste toutes les modifications qui ont été faites sur le fichier ligne par ligne. À chaque modification est associé le début du sha du commit correspondant. Par exemple : 
```csh
   ^05b1233 (Marc Gauthier 2014-08-08 00:31:02 1) # Une liste
```

   Pour retrouver pourquoi cette modification a été faite, vous avez deux possibilités : 

   Faire un git log et rechercher le commit dont le sha commence par 05b1233. 

   Utiliser la commande git show qui vous renvoie directement les détails du commit recherché en saisissant le début de son sha : 
```csh
   git show 05b1233
```

   On en revient à un point essentiel : pensez à écrire des messages clairs et précis lorsque vous faites vos commits. Cela vous facilitera la vie lorsque vous y reviendrez dessus plus tard, et la vie de vos collaborateurs ! Et si vous tombez sur une modification pour laquelle le message de commit n'est pas assez explicite, gardez en tête que vous pouvez contacter l'auteur du commit pour en savoir plus. 


# Ignorez des fichiers
 

[link to video](https://openclassrooms.com/fr/courses/2342361-gerez-votre-code-avec-git-et-github/2433721-ignorez-des-fichiers)

 Ne manquez pas ce chapitre ! Pour des raisons de sécurité et de clarté, il est important d'ignorer certains fichiers dans Git, tels que :

 Tous les fichiers de configuration (config.xml, databases.yml, .env...)

 Les fichiers et dossiers temporaires (tmp, temp/...)

 Les fichiers inutiles comme ceux créés par votre IDE ou votre OS (.DS_Store, .project...)

 Le plus crucial est de ne JAMAIS versionner une variable de configuration, que ce soit un mot de passe, une clé secrète ou quoi que ce soit de ce type. Versionner une telle variable conduirait à une large faille de sécurité, surtout si vous mettez votre code en ligne sur GitHub !

  

  Si vous avez ce type de variables de configuration dans votre code, déplacez-les dans un fichier de configuration et ignorez ce fichier dans Git : nous allons voir comment faire cela dans la vidéo ci-dessous en utilisant le fichier .gitignore.

  Si le code a déjà été envoyé sur GitHub, partez du principe que quelqu'un a pu voir vos données de configuration et mettez-les à jour (changez votre mot de passe ou bien générez une nouvelle clé secrète).

   Créez le fichier .gitignore pour y lister les fichiers que vous ne voulez pas versionner dans Git (les fichiers comprenant les variables de configuration, les clés d'APIs et autres clés secrètes, les mots de passe, etc.). Listez ces fichiers ligne par ligne dans .gitignore en indiquant leurs chemins complets, par exemple : 

   motsdepasse.txt
   config/application.yml
   Le fichier .gitignore doit être tracké comme vos autres fichiers dans Git : vous devez donc l'ajouter à l'index et le committer. 
