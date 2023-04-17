# Feedback 1

## Détail d'une carte

L'ajout de la nouvelle page "Détail d'une carte" est realisé avec succès.

Je note une bonne compréhension de l'architecture de code existante, ce qui est reflété par les bonnes pratiques de développement que vous avez suivies.

Tout d'abord, vous avez correctement ajouté le lien vers la page de détails de la carte à partir de la page d'accueil. La création de la vue `.ejs` dans le dossier `views/` est également conforme à la structure de l'application.

De plus, vous avez créé une nouvelle méthode dans le controller pour appeler la méthode `getOneCard` du `dataMapper` afin de récupérer les informations de la carte demandée.

Vous avez ensuite transmis ces informations à la vue `.ejs` afin de générer la page de détails de la carte.

Enfin, la nouvelle route paramétrée que vous avez créée pour accéder à la page de détails de la carte est parfaitement en ligne avec les autres routes existantes.


Dans cette partie, je n'ai pas beaucoup de reproches à te faire, à part que c'était le nom `getCard` qui était proposé dans l'énoncé, à la place de `getOneCard`.



## Recherche

La recherche avec le formulaire est également fonctionnelle :

- Le mot-clé de recherche est bien récupéré avec un req.query.element.

- Après la soumission du formulaire, on est bien redirigé vers la page de résultat de recherche.

- Les éléments affichés sont conformes au critère de recherche.


Cependant, il y a une erreur au niveau du titre de la page lorsqu'aucun élément n'est choisi pour la recherche. Il affiche "Résultat de la recherche : NaN".

### Pourquoi y a-t-il une erreur ?

L'erreur provient de la ligne 22 du fichier `searchController.js` :

```js
title: 'Résultat de la recherche : ' + (searchedElement === 'null' ? ' sans élément' : + searchedElement),
```

Le bug est causé par le signe "+" de trop après les ":" d'où le `NaN` qui est affiché sur la page.

### Solution

La ligne devrait plutôt être remplacée par :

```js
title: 'Résultat de la recherche : ' + (searchedElement === 'null' ? ' sans élément' : searchedElement),
```

ou par la ligne suivante qui est beaucoup plus optimale. Ca utilise les `backticks` tu peux voir l'utilisation de cette syntaxe sur MDN via https://developer.mozilla.org/fr/docs/Web/JavaScript/Reference/Template_literals

```js
title: `Résultat de la recherche : ${searchedElement || 'sans élément'}`
```


## Construire un deck

Je note une bonne gestion de la logique du deck sur cette partie et c'est top:

- L'ajout du symbole [ + ] sur chaque carte sur la plage d'accueil

- La création de l'action `addCard` du contrôleur `cardController` avec la logique qui va avec en utilisant les sessions sans risque de duplication de cartes.

Tu pourrais ajouter des messages flash pour informer l'utilisateur dans le cas où la carte serait déjà présente dans le deck.

Sur ta fonction `deckPage` suivante :

```js
deckPage: (req, res) => {
  // Initialisation des cartes du deck, pour l'instant vide
  let cards = [];
  if(req.session.cards) {
    // Ajout des cartes en session au deck
    cards = req.session.cards;
  }
  res.render('card/deck', { cards });
},
```

Tu pourrais le raccourcir en :

```js
deckPage: (req, res) => {
  res.render('card/deck', { cards: req.session.cards || [] });
},
```
