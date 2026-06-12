Quick tips pour prendre en main les fichiers 

Pour réaliser mon visuel TouchDesigner j'ai utilisé la version experimental 2025.30060 car c'est avec ce modèle que je rencontrais le moins de bug.

Dans asemic-writting_video-ligature.toe, certains aspects sont assez intéréssant à modifier mais peuvent paraitre brumeux si vous n'etes pas familiers au focntionnement de TouchDesigner. 

Audio-reactivité :

J'ai d'abord crée ma ligne sans quelle soit audio-réctive. Dans un premier temps, afin qu'elle bouge de manière random je suis allée modifier noise2 > transform > translate > + > tz > (cmdc/cmdv) absTime.seconds/5. Ce qui permet à ma ligne de bouger de manière random en fonction des secondes, je l'ai divisé par 5 (/5) pour que le mouvement soit plus lent. Vous pouver modifier cette valeure afin de changer la vitesse. 

Pour que ma ligne devienne audio-réactive j'ai d'abord crée une chaine simple d'opérateurs, audiofilein1 > audiodevout1 > analyze1. Afin de lier mes enregistrements à mon visuel j'ai cliqué sur le Viewer Activ de analyze1 ce qui me permet de drag and drop des informations dans d'autres opérateurs. J'ai selectioné analyze1 > chan1 (le curseur devient ▲) > copy1 > stamp > value > + > chop references. Puis j'ai divisé par 80 (/80) car c'est ce qui correspondait le mieux à la sensibilité de mon audio. Vous pouvez également modifier cette valeure en focntion de la sensibilité de vos audios. Enfin, une dernière manipulation est necessaire afin que tout soit audio-reactif, dans noise2 > noise > seed > + > (cmdc/cmdv) fetchStamp('index', 1). 

Esthétique de la ligne en fonction du son : 

Tout se joue dans noise2 > noise. les features harmonics / roughness / amplitude sont les plus intéressant à modifier pour faire varier les mouvements de la ligne en fonction du son. Mais vous pouver également tester avec d'autres features afin de singulariser votre tracé selon vos envies.

Esthétique de la ligne : 

En fonction de la puissance de votre ordinateur, il est possible de modifer le nombre de points qui composent votre ligne. Dans line1 > line > numbers of points vous pouvez modifier cette valeur, j'au utilisé 100 car c'est ce qui correspondait le mieux à ce que mon ordinateur pouvait supporter.

La ligne à cet aspect de signature manuscrite car je lui ai indiqué quelle devait etre ainsi, mais de nombreuses autres varitions visuelles sont possibles. Dans convert1 > convert > convert to, il est possible de selectionner différentes formes qui rendront votre tracé différent, le mien est nurbs curve.

L'épaisseur est l'aspect de la ligne peuvent également etre modifiés, dans rectangle1 > rectangle > size vous pouvez modifier l'épaisseur de votre trait, l'augmenter ou le réduire en modifiant les deux valeurs en paire (carré) mais aussi séparement afin de créer une forme (rectangle) qui s'apparentrait plus au tracé d'une plume.

J'ai crée un tracé qui se rapproche le plus possible de ce qu'un crayon pourrait créer sur du papier, que je n'a pas utilisé au final mais ai laissé dans le fichier. Je l'ai crée via une suite d'opérateur se terminant par constant1, si bous voulez l'utiliser il suffit d'aller dans geo1 > render > material > (cmdc/cmdv) constant1 à la place de constant2, c'est aussi à cet emplacement que vous pourrez mettre d'autres aspects de tracés que vous aurez crées.

Pour terminer, vous pouvez modifier la couleur de fond et la couleur du tracé, c'est assez simple. Pour modifier la couleur du tracé il faut aller dans constant1 ou constant2 > constant > color et selectionner une nouvelle. Pour le fond vous pouvez aller dans render1 > render > background color > selectionner une nouvelle > pre-multiply rgb by alpha > off.

Il y aurait d'autres features interessantes à détailler concerant ce fichier touchdesigner mais je vous laisse experimenter plus profondément par vous memes.
