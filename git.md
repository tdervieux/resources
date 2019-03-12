#Qui a fait une modification

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
