***Quick tips pour prendre en main les fichiers***

Pour réaliser ces visuels j'ai utilisé la version <em>experimental 2025.30060</em> de TouchDesigner car c'est avec ce modèle que je rencontrais le moins de bugs, notamment depuis la nouvelle mise à jour des opérateurs POP.

**1. abstract-visual_audio-reactif.toe**

Ce fichier devait être le visuel principal pour la vidéo. Par peur qu'il soit trop complexe, trop lourd, trop abstrait et donc trop détaché de la représentation du langage (écrit ou oral), je l'ai abandonné au profit d'<em>asemic-writting</em> qui se connecte davantage à mon propos. De nombreux éléments composent ce fichier, je vais donc me concentrer sur les éléments qui sont intéressants à modifier pour faire varier ce visuel.

**Transformer la vidéo source en visuel abstrait :**

J'ai réalisé en amont une série d'opérateurs qui décomposent chromatiquement ma vidéo source. Pour que cette vidéo ait l'aspect de formes géométriques/organiques mouvantes, j'ai extrait des informations via <em>info1</em> que j'ai passé en <em>Viewer Active</em>, j'ai ensuite drag and drop <em>info1 > resx</em> (le curseur devient ▲) <em>> grid1 > grid > size > + > sizex > chop references</em>, j'ai répété cette manipulation avec <em>info1 > resy</em> (le curseur devient ▲) <em>> grid1 > grid > size > + > sizey > chop references</em>. Puis ai divisé par 40 <em>(/40</em>) pour que les particules s'étendent ensuite via <em>noise2</em>. Afin que ces formes soient complètement liées aux changements chromatiques de ma vidéo source, j'ai également drag and drop <em>info1 > resx</em> (le curseur devient ▲) <em>> grid1 > grid > rows > + > chop references</em> mais aussi <em>info1 > resy</em> (le curseur devient ▲) <em>> grid1 > grid > columns > + > chop references</em>. Et voilà comment sont liées les modifications colorimétriques de ma vidéo source à mon visuel abstrait.

Dans <em>noise2</em> il est possible de modifier l'aspect des particules, il suffit d'aller dans <em>noise2 > noise > type</em> et de choisir une autre apparence, j'ai sélectionné <em>brownian</em> car je voulais créer une esthétique brumeuse avec des dégradés en fonction des changements colorimétriques. <em>Amplitude</em> est également intéressant à modifier afin d'étendre plus ou moins les particules.

Mes particules s'articulent selon un système assez complexe où toutes les informations s'interconnectent. Vous pouvez découvrir comment j'ai entrelacé toutes ces données entre elles mais je vous conseillerais de ne pas y toucher si vous n'êtes pas familier avec TouchDesigner.

Cependant, après <em>null5</em> j'ai rajouté des effets prédéfinis : en ouvrant la palette (opt + l / alt + l) <em>> derivative > imagefilters ></em> j'ai sélectionné <em>radialblur</em> afin que mon visuel soit encore plus organique. Sentez-vous libre de vous amuser avec tous les paramètres de ce filtre afin de modifier votre visuel. J'ai rajouté un <em>soften alpha</em> (également disponible dans la palette) pour flouter les contours de mes formes ; le paramètre le plus intéressant est <em>softenalpha > soften > width</em>.

**Colorimétrie du visuel :**

Pour que mon visuel change de couleur en fonction du son, je suis venue rajouter un <em>ramp1</em> après une succession assez simple d'opérateurs sonores <em>(audiofilin1 > audiodevout1 > null4)</em>. Dans <em>ramp1</em> je suis venue créer un dégradé via <em>ramp > rgb/hsv</em> ; pour le connecter au son j'ai drag and drop <em>null4 > chan1</em> (le curseur devient ▲) <em>> ramp1 > ramp > phase > + > chop references</em>. Vous pouvez modifier le dégradé, il se connectera toujours à <em>constant2</em> qui le fera s'appliquer au visuel car j'ai pris soin de drag and drop en amont le dégradé de <em>ramp1</em> à <em>constant2</em> via <em>constant > color > + > colorr / colorg / colorb</em> (drag and drop 3 fois le même dégradé dans les 3 cases).

Pour rendre mon visuel plus ou moins intense colorimétriquement parlant, j'ai joué avec des opérateurs <em>level3</em> et <em>level4</em> que je suis venue superposer via <em>over2</em>. Enfin pour le fond, vous pouvez le modifier dans <em>constant3</em>.

**2. tracking-top.toe**

J'avais conçu ce fichier dans le but de tracker les lèvres des utilisateur·ices lorsque je commençais ce projet ; ne sachant pas exactement quelle forme allait prendre ma vidéo, j'avais créé un tracking qui suivait les ondulations du corps afin de créer de nouvelles formes liées aux mouvements labiaux.

**Créer les contours du sujet pour le tracking :**

Avant de créer des points à relier, il faut d'abord concevoir les contours du sujet. Pour cela, j'ai créé une chaîne d'opérateurs <em>diff1 > blur1 > thresh1</em>. <em>Diff1</em> permet d'extraire la différence colorimétrique de la vidéo source, ce qui crée une sorte de contour ; <em>blur1</em> vient les atténuer et donc les étendre ; les paramètres intéressants à modifier sont <em>blur1 > blur > pre-shrink</em> et <em>size filter</em>. <em>Threshold</em> a pour but de transformer les contours en noir et blanc ; si vous modifiez les valeurs de <em>thresh1 > threshold > threshold</em>, vous obtiendrez des variations plus ou moins intenses, ce qui à terme modifiera la sensibilité de connexion entre les points.

**Formes géométriques :**

Toutes ces valeurs passent ensuite dans un script, que je vous déconseille de modifier si vous n'êtes pas familier avec TouchDesigner car j'ai rajouté moi-même un script python dans <em>script1_callbacks</em> ; il est cependant visible dans la case de texte grise si jamais vous voulez le comprendre ou vous en emparer.

Pour connecter ces données à des formes géométriques, c'est assez simple. J'ai créé des rectangles qui s'étendent en fonction des zones de mouvements dans <em>rectangle1</em>. Ces formes ont des contours ; vous pouvez les modifier dans <em>line1 > line</em> et jouer avec les paramètres de cette fenêtre. J'ai choisi d'interconnecter ces formes entre elles via des lignes ; elles sont simples mais peuvent prendre des aspects différents : en cliquant sur <em>convert1 > convert > convert to</em>, vous pouvez choisir d'autres formes esthétiquement intéressantes. Enfin, si vous voulez simplement modifier les couleurs ou l'épaisseur, les paramètres à modifier sont les mêmes que pour <em>line1</em> mais avec <em>line2</em>.

Il y aurait d'autres features intéressantes à détailler concernant ces fichiers TouchDesigner mais je vous laisse expérimenter plus profondément par vous-mêmes.
