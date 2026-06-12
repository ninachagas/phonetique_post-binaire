***Quick tips pour prendre en main les fichiers***

Pour réaliser mon visuel j'ai utilisé la version <em>experimental 2025.30060</em> de TouchDesigner car c'est avec ce modèle que je rencontrais le moins de bugs, notamment depuis la nouvelle mise à jour des opérateurs POP.

Dans asemic-writting_video-ligature.toe, certains aspects sont assez intéressants à modifier mais peuvent paraître brumeux si vous n'êtes pas familiers avec le fonctionnement de TouchDesigner.

Audio-réactivité :

J'ai d'abord créé ma ligne sans qu'elle soit audio-réactive. Dans un premier temps, afin qu'elle bouge de manière aléatoire j'ai modifié noise2 > transform > translate > + > tz > (cmdc/cmdv) absTime.seconds/5. Ce qui permet à ma ligne de bouger de manière random en fonction des secondes, je l'ai divisé par 5 (/5) pour que le mouvement soit plus lent. Vous pouvez modifier cette valeur afin de changer la vitesse.

Pour que ma ligne devienne audio-réactive j'ai d'abord créé une chaîne simple d'opérateurs : audiofilein1 > audiodevout1 > analyze1. Afin de lier mes enregistrements à mon visuel j'ai cliqué sur le Viewer Active de analyze1 ce qui permet de drag and drop des informations dans d'autres opérateurs. J'ai sélectionné analyze1 > chan1 (le curseur devient ▲) > copy1 > stamp > value > + > chop references. Puis j'ai divisé par 80 (/80), c'est ce qui correspondait le mieux à la sensibilité de mon audio. Vous pouvez également modifier cette valeur en fonction de la sensibilité d'autres audios. Enfin, une dernière manipulation est nécessaire afin que tout soit audio-réactif : dans noise2 > noise > seed > + > (cmdc/cmdv) fetchStamp('index', 1). Et voilà ! la ligne immobile est devenue mouvante et liée au son.

Esthétique de la ligne en fonction du son :

Tout se joue dans noise2 > noise. Les features harmonics / roughness / amplitude sont les plus intéressantes à modifier pour faire varier les mouvements de la ligne en fonction du son. Mais vous pouvez également tester avec d'autres features afin de singulariser votre tracé selon vos envies.

Esthétique de la ligne :

En fonction de la puissance de votre ordinateur, il est possible de modifier le nombre de points qui composent votre ligne. Dans line1 > line > numbers of points vous pouvez modifier cette valeur, j'ai utilisé 100 car c'est ce qui correspondait le mieux à ce que mon ordinateur pouvait supporter.

La ligne a cet aspect de signature manuscrite car je lui ai indiqué qu'elle devait être ainsi, mais de nombreuses autres variations visuelles sont possibles. Dans convert1 > convert > convert to, il est possible de sélectionner différentes formes qui rendront votre tracé différent, le mien est nurbs curve.

L'épaisseur et l'aspect de la ligne peuvent également être modifiés. Dans rectangle1 > rectangle > size vous pouvez modifier l'épaisseur de votre trait, l'augmenter ou le réduire en modifiant de pair les deux valeurs (carré) mais aussi séparément afin de créer une forme (rectangle) qui s'apparenterait plus au tracé d'une plume avec des pleins et des déliés.

J'ai créé une ligne qui se rapproche le plus possible de ce qu'un crayon pourrait tracer sur du papier, je ne l'ai pas utilisée au final mais elle est toujours dans mon fichier. Je l'ai créée via une suite d'opérateurs se terminant par constant1. Si vous souhaitez l'utiliser, il suffit d'aller dans geo1 > render > material > (cmdc/cmdv) constant1 à la place de constant2. C'est aussi à cet emplacement que vous pourrez mettre d'autres aspects de tracés que vous aurez créés.

Pour terminer, vous pouvez modifier la couleur de fond et la couleur du tracé, c'est assez simple. Pour la couleur du tracé il faut aller dans constant1 ou constant2 > constant > color et en sélectionner une nouvelle. Pour le fond vous pouvez aller dans render1 > render > background color > en sélectionner une nouvelle > pre-multiply rgb by alpha > off.

Il y aurait d'autres features intéressantes à détailler concernant ce fichier TouchDesigner mais je vous laisse expérimenter plus profondément par vous-mêmes.
