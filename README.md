# urban-semantic-mapping
Progetto per il Laboratorio di IA 

Traccia:

Autonomous Driving and Urban Semantic Mapping

Sviluppo di un sistema per la mappatura visuale delle [lampade/alberi/cartelli stradali] di Roma a partire da una sequenza di immagini fisse. 
Detagli: 
L’idea di base è quella di usare un detector tipo yolo per individuare una qualche categoria di oggetti stradali (o più di una), come i lampioni, gli alberi, o i cartelli stradali. Per alcune categorie dovrebbero esistere già delle implementazioni di Yolo preaddestrate, quindi si tratta di capire come funziona (Ovviamente si può anche riaddestrare, se lo si desidera). (e.g. https://github.com/topics/traffic-sign-detection, https://roboflow.com/)
Il detector da solo non da la posizione 3D degli oggetti, ma solo la posizione 2D rispetto all’immagine su cui è applicato. Per avere la posizione 3D è necessario triangolare l’oggetto dal piano immagine a una terna di riferimento 3D che sarà la terna della mappa. Questo può essere fatto in molti modi, e si può fare riferimento al web e al libro di Szelinski per farsi venire qualche idea. Per chi abita a Roma, posso fornire delle telecamere stereo da usare per raccogliere dati che abbiano anche l’informazione di profondità da usare per la triangolazione, altrimenti si possono usare anche altri sistemi. 
Il sistema di mappatura dovrebbe essere in grado, data una sequenza continua di frame in ingresso, di fornire in uscita la posizione 3D riferita ad una terna di riferimento della mappa (tipicamente si prende come origine e orientamento quello del primo frame raccolto) di ogni oggetto indifiduato, evitando le duplicazioni. Questo vuol dire che se in frame successivi vedo lo stesso oggetto mentre mi muovo, non lo aggiungo come un nuovo oggetto. Eventualmente si può utilizzare le individuazioni successive come misure agiguntive per raffinare la poszione dell’oggetto nella mappa. (https://www.cs.columbia.edu/~allen/F19/NOTES/slam_pka.pdf, https://www.researchgate.net/publication/231575337_A_tutorial_on_graph-based_SLAM)
