***Quick tips pour prendre en main les fichiers*** 

abstract-visual_audio-reactif.toe

Pendant longtemps ce fichier devait etre le visuel principal pour la vidéo mais par peur qu'il soit trop complexe, trop lourd, trop abstrait et donc trop détaché du langage écrit avec lequel je fait des ponds via le langage oral, je l'ai abandoné au proffit d'asemic-writting qui fait davantage sens avec mon propos. De nombreux éléments composent ce fichier, je vais donc me concentrer sur les éléments qui sont interessants à modifier pour faire varier ce visuel.

J'ai réalisé en amont une série d'opérateur qui décomposent chromatiquement ma vidéo source. Pour que cette vidéo ai l'aspect de formes géométriques/organiques mouvantes. j'ai éxtrait des informations via info1 que j'ai passé en Viewer Active, j'ai ensuite drag and drop info1 > resx (le curseur devient ▲) > grid1 > grid > size > + > sizex > chop references, j'ai répété cette manipulation avec info1 > resy > grid1 > grid > size > + > sizey > chop references. Puis ai divisé par 40 (/40) pour que les particules s'étendent ensuite via le noise2. Afin que ces formes soient completement liés aux changements chromatiques de ma vidéo source, j'ai également drag and drop info1 > resx > grid1 > grid > rows > + > (cmdc/cmdv) op('info1')['resx'] mais aussi info1 > resy > grid1 > grid > columns > + > (cmdc/cmdv) op('info1')['resy']

tracking-top.toe
