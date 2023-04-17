# Feedback 1

## Détail d'une carte

L'ajout de la nouvelle page "Détail d'une carte" est realisé avec succès.

Je note une bonne compréhension de l'architecture de code existante, ce qui est reflété par les bonnes pratiques de développement que vous avez suivies.

Tout d'abord, vous avez correctement ajouté le lien vers la page de détails de la carte à partir de la page d'accueil. La création de la vue `.ejs` dans le dossier `views/` est également conforme à la structure de l'application.

De plus, vous avez créé une nouvelle méthode dans le controller pour appeler la méthode `getAllCards` du `dataMapper` afin de récupérer les informations de la carte demandée.

Vous avez ensuite transmis ces informations à la vue `.ejs` afin de générer la page de détails de la carte.

Enfin, la nouvelle route paramétrée que vous avez créée pour accéder à la page de détails de la carte est parfaitement en ligne avec les autres routes existantes.


Dans cette partie, je n'ai pas beaucoup de reproches à te faire, à part que tu pourrais afficher tous les details de l'objet de la carte sur la page.


## Recherche

Il est à noter que l'implémentation de la recherche ne corresponds pas aux attentes de l'énoncé.

Parce qu'il y'a une erreur dans le cas où "aucun" est sélectionné dans le formulaire. Le résultat attendu était de rechercher les cartes dont l'élément est égal à "null" (il y en a 74).

Cependant, l'utilisation de la méthode `.filter()` était une bonne idée dans le code proposé.


## Construire un deck

On a bien une page `/desk` qui liste l'ensemble des cartes stockées dans la session.

Cependant, il y a un petit bug car il est possible d'ajouter plus de 5 cartes dans la session.

Il faudra donc retravailler la fonction `addDeck()` afin qu'elle ajoute une nouvelle carte dans la session seulement lorsque cette dernière n'a pas déjà plus de 5 cartes.

## En somme

Malgré le bug avec la session sur la page de desk et celui de la recherche, je note quand même une bonne maîtrise de certains concepts javascript comme la programmation fonctionnelle qui est une bonne approche.

Aussi, l'intégration des nouvelles fonctionnalités montre une bonne compréhension de la logique MVC avec ExpressJS.