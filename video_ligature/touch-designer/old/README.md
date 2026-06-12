***Quick tips pour prendre en main les fichiers*** 

abstract-visual_audio-reactif.toe

Pendant longtemps ce fichier devait etre le visuel principal pour la vidéo mais par peur qu'il soit trop complexe, trop lourd, trop abstrait et donc trop détaché du langage écrit avec lequel je fait des ponds via le langage oral, je l'ai abandoné au proffit d'asemic-writting qui fait davantage sens avec mon propos. De nombreux éléments composent ce fichier, je vais donc me concentrer sur les éléments qui sont interessants à modifier pour faire varier ce visuel.

Transformer la vidéo source en visuel abstrait :

J'ai réalisé en amont une série d'opérateurs qui décomposent chromatiquement ma vidéo source. Pour que cette vidéo ai l'aspect de formes géométriques/organiques mouvantes. j'ai éxtrait des informations via info1 que j'ai passé en Viewer Active, j'ai ensuite drag and drop info1 > resx (le curseur devient ▲) > grid1 > grid > size > + > sizex > chop references, j'ai répété cette manipulation avec info1 > resy (le curseur devient ▲) > grid1 > grid > size > + > sizey > chop references. Puis ai divisé par 40 (/40) pour que les particules s'étendent ensuite via noise2. Afin que ces formes soient completement liés aux changements chromatiques de ma vidéo source, j'ai également drag and drop info1 > resx (le curseur devient ▲) > grid1 > grid > rows > + > chop references mais aussi info1 > resy (le curseur devient ▲) > grid1 > grid > columns > + > chop references. Et voila comme sont lié mes modifications colorimétriques de ma vidéo source à mon visuel abstrait.

dans noise2 il est possible de modifier l'aspect des particules, il suffit d'aller dans noise2 > noise > type et de choisir un autre aspect, j'ai selctionné brownian car je voulais garder l'aspect brumeux et dégradé des changements colorimétrqiues. L'amplitude est également intéressant à modifier afin d'étendre plus ou moins les particules.

Mes particules s'articulent selon un sytème assez complexes ou toutes les informations s'interconnectent, vous pouvez découvrir comment j'ai entrelacé toutes ces donnés entres elles mais je vous conseillerais de ne pas y toucher si vous n'etes ps familier à TouchDesigner.

Cependant, apres null5 j'ai rajouté des effets prédéfinis, en ouvrant la palette > deriative > imagefilters > j'ai selectionné radialblur afin que mon visuel soit encore plus organique. sentez vous libre de vous amuser avec tout les parametres de ce filtre afin de modifier votre visuel. J'ai rajouté un soften alpha (également disponible dans dans la palette) pour floutter les contours de mes formes, le parametre le plus interessant est softenalpha > soften > width.

Colorimétrie du visuel :

Pour que mon visuel change de couleur en fonction du son, je suis venue rajouter un ramp1 après une succession assez simple d'opérateurs sonores (audiofilin1 > audiodevout1 > null4). dans Ramp1 je suis venue créer un dégradé dans ramp > rgb/hsv, pour le onnecter au son j'ai drag and drop null4 > chan1 (le curseur devient ▲) > ramp1 > ramp > phase > + > chop references. Vous pouvez modifier le dégrader, il se connectera toujours à constant2 qui le fera s'appliquer au visuel car j'ai prit soin de drag and drop en amont le dégradé de ramp1 à constant2 via constant > color > + > colorr / colorg / colorb (drag and drop 3 fois le meme dégradé dans les 3 cases).

Pour rendre mon visuel plus ou mons intense colorimétriquement, j'ai joué avec des opérateurs level3 et level4 que je suis venue supperposée via over2. Enfin pour le fond, vous pouvez le modifier dans constant3.

tracking-top.toe

J'avais concue ce fichier dans le but de tracker les levres des utilisateurs lorsque je commencais ce projet, ne sachant pas exactement quelle forme allait prendre ma vidéo j'avais crée un tracking qui sivrait les mouvements de la bouche afin de créer de nouvelles formes liés aux mouvements labiaux.

Créer les contours du sujet pour le tracking :  

Formes géométriques 
