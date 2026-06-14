***Quick tips pour prendre en main les fichiers***

**1. abstract-visual_audio-reactif.toe**

Ce fichier devait être le visuel principal pour la vidéo. Par peur qu'il soit trop complexe, trop lourd, trop abstrait et donc trop détaché de la représentation du langage (écrit ou oral), je l'ai abandonné au profit d'<em>asemic-writting</em> qui se connecte davantage à mon propos. De nombreux éléments composent ce fichier, je vais donc me concentrer sur les éléments qui sont intéressants à modifier pour faire varier ce visuel.

**Transformer la vidéo source en visuel abstrait :**

J'ai réalisé en amont une série d'opérateurs qui décomposent chromatiquement ma vidéo source. Pour que cette vidéo ait l'aspect de formes géométriques/organiques mouvantes, j'ai extrait des informations via <em>info1</em> que j'ai passé en <em>Viewer Active</em>, j'ai ensuite drag and drop <em>info1 > resx</em> (le curseur devient ▲) <em>> grid1 > grid > size > + > sizex > chop references</em>, j'ai répété cette manipulation avec <em>info1 > resy</em> (le curseur devient ▲) <em>> grid1 > grid > size > + > sizey > chop references</em>. Puis ai divisé par 40 <em>(/40</em>) pour que les particules s'étendent ensuite via <em>noise2</em>. Afin que ces formes soient complètement liées aux changements chromatiques de ma vidéo source, j'ai également drag and drop <em>info1 > resx</em> (le curseur devient ▲) <em>> grid1 > grid > rows > + > chop references</em> mais aussi <em>info1 > resy</em> (le curseur devient ▲) <em>> grid1 > grid > columns > + > chop references</em>. Et voilà comment sont liées les modifications colorimétriques de ma vidéo source à mon visuel abstrait.

Dans noise2 il est possible de modifier l'aspect des particules, il suffit d'aller dans noise2 > noise > type et de choisir une autre apparence, j'ai sélectionné brownian car je voulais créer une esthétique brumeuse avec des dégradés en fonction des changements colorimétriques. L'amplitude est également intéressante à modifier afin d'étendre plus ou moins les particules.

Mes particules s'articulent selon un système assez complexe où toutes les informations s'interconnectent. Vous pouvez découvrir comment j'ai entrelacé toutes ces données entre elles mais je vous conseillerais de ne pas y toucher si vous n'êtes pas familier avec TouchDesigner.

Cependant, après null5 j'ai rajouté des effets prédéfinis : en ouvrant la palette (opt + l / alt + l) > derivative > imagefilters > j'ai sélectionné radialblur afin que mon visuel soit encore plus organique. Sentez-vous libre de vous amuser avec tous les paramètres de ce filtre afin de modifier votre visuel. J'ai rajouté un soften alpha (également disponible dans la palette) pour flouter les contours de mes formes ; le paramètre le plus intéressant est softenalpha > soften > width.

**Colorimétrie du visuel :**

Pour que mon visuel change de couleur en fonction du son, je suis venue rajouter un ramp1 après une succession assez simple d'opérateurs sonores (audiofilin1 > audiodevout1 > null4). Dans Ramp1 je suis venue créer un dégradé dans ramp > rgb/hsv ; pour le connecter au son j'ai drag and drop null4 > chan1 (le curseur devient ▲) > ramp1 > ramp > phase > + > chop references. Vous pouvez modifier le dégradé, il se connectera toujours à constant2 qui le fera s'appliquer au visuel car j'ai pris soin de drag and drop en amont le dégradé de ramp1 à constant2 via constant > color > + > colorr / colorg / colorb (drag and drop 3 fois le même dégradé dans les 3 cases).

Pour rendre mon visuel plus ou moins intense colorimétriquement parlant, j'ai joué avec des opérateurs level3 et level4 que je suis venue superposer via over2. Enfin pour le fond, vous pouvez le modifier dans constant3.

**2. tracking-top.toe**

J'avais conçu ce fichier dans le but de tracker les lèvres des utilisateurs lorsque je commençais ce projet ; ne sachant pas exactement quelle forme allait prendre ma vidéo, j'avais créé un tracking qui suivait les ondulations du corps afin de créer de nouvelles formes liées aux mouvements labiaux.

**Créer les contours du sujet pour le tracking :**

Avant de créer des points à relier, il faut d'abord concevoir les contours du sujet. Pour cela, j'ai créé une chaîne d'opérateurs diff1 > blur1 > thresh1. diff1 permet d'extraire la différence colorimétrique de la vidéo source, ce qui crée une sorte de contour ; blur1 vient les atténuer et donc les étendre ; les paramètres intéressants à modifier sont blur1 > blur > pre-shrink et size filter. Threshold a pour but de transformer les contours en noir et blanc ; si vous modifiez les valeurs de thresh1 > threshold > threshold, vous obtiendrez des variations plus ou moins intenses, ce qui à terme modifiera la sensibilité de connexion entre les points.

**Formes géométriques :**

Toutes ces valeurs passent ensuite dans un script, que je vous déconseille de modifier si vous n'êtes pas familier avec TouchDesigner car j'ai rajouté moi-même un script python dans script1_callbacks ; il est cependant visible dans la case de texte grise si jamais vous voulez le comprendre ou vous en emparer.

Pour connecter ces données à des formes géométriques, c'est assez simple. J'ai créé des rectangles qui s'étendent en fonction des zones de mouvements dans rectangle1. Ces formes ont des contours ; vous pouvez les modifier dans line1 > line et jouer avec les paramètres de cette fenêtre. J'ai choisi d'interconnecter ces formes entre elles via des lignes ; elles sont simples mais peuvent prendre des aspects différents : en cliquant sur convert1 > convert > convert to, vous pouvez choisir d'autres formes esthétiquement intéressantes. Enfin, si vous voulez simplement modifier les couleurs ou l'épaisseur, les paramètres à modifier sont les mêmes que pour line1 mais avec line2.

Il y aurait d'autres features intéressantes à détailler concernant ces fichiers TouchDesigner mais je vous laisse expérimenter plus profondément par vous-mêmes.
