# Sommaire

## histoire de la POO


## nos références

###  ouvrages

Elegant Object vol.1 et 2

### articles de référence

https://radicalobjectorientation.substack.com/


## anti pattenrs


### null


### exceptions


### logique dans les constructeurs


### états et mutabilité


### active records


### appel des constructeurs

toute ligne de code qui prend la responsabilité d'appel un constructeur d'un nouvel objet (new) est un SMELL en puissance ...

Expliquer pourquoi


## patterns


### immutabilité


### value objects


### null objects


### error handling and management


### monades


### builder ou mother object


### Builder plutot que constructeur


### injection de dépendance



### DSL: des objets élégants, à état mais immuables

l'idée est de construire des objets dans l'esprit de SmallTalk, à communication unidirectionnelle
selon le Principle of Mutual Oblivion (PoMO) et de Functionnal independency
https://www.linkedin.com/posts/tastapod_why-event-sourcing-is-not-object-oriented-activity-7338832824013119490-31Ll?utm_source=share&utm_medium=member_desktop&rcm=ACoAAAEg5bUBQXG2QnMueen743s0x85ROxzm_9M

Le principe majeur pour créer un DSL est de se parer d'un ensemble d'objects qui communiquent dans 1 sens uniquement et son indépendants.
faire schéma.
![iamge à refaire](https://substackcdn.com/image/fetch/w_1456,c_limit,f_webp,q_auto:good,fl_progressive:steep/https%3A%2F%2Fsubstack-post-media.s3.amazonaws.com%2Fpublic%2Fimages%2Fec51fe7a-5b90-451f-b07e-2f18fd2ea3fa_1812x258.png)

Chaque objet retient un état de manière externe, mais ne laisse personne influencer cet état (immutabilité).

Pour évoluer d'un état à l'autre (principe de la machine à état) on va donner naissance à un nouvelle objet pour chaque nouvel état.

A son tour, tout nouvel objet gère son propre état avec potentiellement des propriétés internes, qu'il peut exposer pour dire qq chose (Tell, don't ask). Mais surtout son état, c'est son type. C'est sa nature.

Par exemple: je suis l'état de départ. Ou: je suis l'état terminal.

Il y a donc un point de départ. 
C'est le seul objet qui peut etre construit, mais mieux encore , un fonction statique de Build() s'en chargera.

Les autres objets qui représentent les états suivants, ne se créént que par appel d'une fonction disponilble sur l'objet précédent dans le graphe qui relie les objets.

Et les fonctions publiquent d'un objet ne devraient pas renvoyer void et modifier l'état interne de l'objet, qui se doit d'etre immuable. Au contraire, elle doivent etre pure, et donc retourne l'effet produit.
Et dans le cas d'un DSL (machine à état), l'effet d'une fonction publique est de produite un nouvel état, et donc un nouvel objet.



## Functions are the new objects





