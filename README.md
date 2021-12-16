Table of Contents
General Info
Lecture Automatique
Création du lecteur
Autorisations et gestion du fichier manifest
General Info
Music player est une application qui permet d'écouter la musique présente sur votre terminal. Ce TP permetra entre autre de voir les permissions d'une application, la gestion d'un menu, la recherche de media directement dans le terminal, la mise en place d'un fichier README.md pour github*, ...

La création de l'application se fera pas à pas, en commençant par la lecture automatique d'une chanson, puis l'ajout de bouton pour le player, l'ajout d'un listeView pour afficher les chansons disponibles dans le terminal et pour finir la mise en place d'un système de recherche dans la liste.

*Pour plus d'informations sur les fichiers README.md je vous renvoie vers le site de ionos et une bonne explications des différents cas : https://www.ionos.fr/digitalguide/sites-internet/developpement-web/fichier-readme/

Screenshot
Lecture Automatique
Ajout d'un fichier son dans une application
Pour ajouter un fichier son il faut commencer par vérifier la casse du fichier, en effet les fichiers faisant parti intégrante d'une application seront placés dans un sous dossier du répertoire res, seul les caractères minuscules, les chiffres et les under-scrore sont autorisés.

Pour jouer un son il faut faire appel à la classe MediaPlayer, Android prend en charge la lecture des types de médias courants, il est possible d’intégrer de l'audio et la vidéo dans vos applications à partir de fichiers multimédias stockés dans les ressources de votre application (ressources brutes), de fichiers autonomes dans le système de fichiers ou d'un flux de données provenant d’internet, le tout à l'aide des API MediaPlayer.

Pour intégrer un lecteur audio dans une application il faut d’abord créer un dossier nommé raw dans le dossier res. Ce dossier contiendra les fichiers médias audio et vidéo.
Clic droit dans l’arborescence > New > Folder > Raw Resources Folder
Dans le popUp qui vient de s'ouvrir, ajouter un dossier raw de type raw
Ajouter le fichier présent sur le drive dans Android/Assets/Audio NB : Si votre fichier n’apparaît pas dans raw clic droit dans l’arborescence > Reload from disk
Modifier MainActivity pour jouer le son lorsque l'application démarre (cf #1 Ajouter du son en automatique dans MainActivity)
Création du lecteur
Android studio ne met pas à disposition de lecteur audio il va donc falloir le créer de toute pièces. Nous allons ajouter des widgets pour rendre la lecture de notre morceau interactive. Deux widgets ImageButton un pour Play, l’autre pour Pause auquels nous associerons une méthode onClick() via le XML.

Les boutons play et pause
Dans activity_main.xml ajouter :

Un LinearLayout Horizontal pour faciliter le placement des boutons (penser à gravity pour centrer le contenu)
Les ImageButton, pour trouver les images correspondantes, faire défiler les bitmaps de la liste qui s’affiche lors de l’ajout d’un ImageButton pour trouver Play et Pause
Dans MainActivity ajouter :

Une méthode Play (cf #2 La méthode Play)
Une méthode Pause (cf #3 La méthode Pause) Ne pas oublier de rattaché les méthodes à l'attribut onClick du xml
Pour simplifier le placement ajouter un Linear Vertical dans lequel on encapsule le linear des boutons puis on y ajoute les seekbar de position et du volume

La gestion de la position dans le morceau
Dans activity_main.xml ajouter :

Une seekbar pour gérer la position dans le morceau
Dans MainActivity ajouter :

Une méthode position pour gérer le déplacement par l'utilisateur de la seekBar et jouer le morceau à l'emplacement désiré mais aussi du déplacement automatique de la position du curseur sur la seekBar lors de la lecture.
La gestion du volume
Dans activity_main.xml ajouter :

Une seekbar pour la gestion du Volume
Dans MainActivity ajouter :

Une méthode volume pour gérer le volume du morceau lors de la lecture, cela implique de connaître le volume maximal du terminal. Cependant il varie selon les terminaux et selon l’application à laquelle il est associé. Pour voir ces différentes utilisations [CTRL][Espace] après STREAM_ lors de la création de la variable volumeMax. Il faut aussi connaître la valeur actuelle du volume pour déplacer le curseur de la seekBar en conséquence.
Autorisations et gestion du fichier manifest
Le lecteur sera visible seulement en mode portrait Les modifications pour l'orientation


Les modifications pour l'orientation


Les modifications pour l'orientation


Ajout de la liste des morceaux de musique présents dans le terminal
