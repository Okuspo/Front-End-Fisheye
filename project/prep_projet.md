# P6 Fisheye

## <a id="index">Index</a>

[1 - Liens utiles](#links)  
[2 - Briefing](#2)  
___[2.1 - Prototype des fonctionnalités](#2.1)  
___[2.2 - Contraintes techniques additionnelles](#2.2)  
___[2.3 - Livrables](#2.3)  
[3 - Etude de la maquette](#3)  
[4 - Etude de la codebase originale](#4)  
___[4.1 - HTML](#4.1)  
___[4.2 - CSS](#4.2)  
___[4.3 - JS](#4.3)  
___[4.4 - JSON](#4.4)  
___[4.5 - Décomposition de la codebase](#4.5)  
[5 - Codebase existante VS résultat final](#5)  
[6 - Planification du projet](#6)  
[Annexe 1 - Concepts à apprendre](#Annexe1)  
[Annexe 2 - Questions mentorat](#Annexe2)

___

## <a id="links">1 - Liens utiles</a>

[Repo GitHub original](https://github.com/OpenClassrooms-Student-Center/Front-End-Fisheye)  
[Maquette Figma](https://www.figma.com/file/Q3yNeD7WTK9QHDldg9vaRl/UI-Design-FishEye-FR)

___

## <a id="2"> 2 - Briefing</a>

**Entreprise :**
Site web de photographes freelances.
“Nos clients prennent de super photos, mais ils n’y connaissent rien en développement web. C'est pourquoi nous proposons une plateforme unique pour montrer leurs photos sur une belle page et les contacter pour des événements ou des tirages.  
Nous sommes l'un des plus grands sites de photographie en freelance, avec un énorme réseau de photographes.”

**Objectif :**
Leur site est obsolète et a besoin d'être remanié.  
"Notre site a été construit il y a plus de dix ans, et nous n'avons pas eu l'occasion de le mettre à jour jusqu'à présent. Nous venons de lever des fonds et nous aimerions que votre équipe le transforme d'un site statique à un site dynamique".

### <a id="2.1">2.1 - Prototype des fonctionnalités</a>

Nous devons créer les pages suivantes pour le prototype :

**Page d'accueil :**

- Liste de tous les photographes avec leur nom, leur slogan, leur localisation, leur prix/heure, leurs tags et une image miniature de leur choix.  
- En cliquant sur une étiquette (tag) dans la barre de navigation, la liste des photographes est filtrée pour n'afficher que ceux qui correspondent à cette étiquette.  
- Lorsque l'utilisateur clique sur la vignette d'un photographe, il est amené à sa page.  

**Pages des photographes** (une pour chaque photographe échantillon) :

- Affiche une galerie des travaux du photographe.
- Les photographes peuvent montrer à la fois des photos et des vidéos.
- Dans le cas des vidéos, montrer une image miniature dans la galerie.
- Chaque média comprend un titre et un nombre de likes.
- Lorsque l'utilisateur clique sur l'icône "Like", le nombre de likes affiché est incrémenté.
- Le nombre de likes total d’un photographe doit correspondre à la somme des likes de chacun de ses médias.
- Les médias peuvent être triés par popularité ou par titre.
- Lorsque l'utilisateur clique sur un média, celui-ci doit s’ouvrir dans une lightbox :
- Lorsque la lightbox est affichée, il y a une croix dans le coin pour fermer la fenêtre.
- Des boutons de navigation permettent de passer d'un élément média à l'autre (les utilisateurs peuvent cliquer sur ces boutons pour naviguer).
- Les touches fléchées permettent également de naviguer entre les médias.
- Afficher un bouton pour contacter le photographe.
- Le formulaire de contact est une modale qui s'affiche par-dessus le reste.
- Il comprend des champs pour les noms, l'adresse électronique et le message.
- Plus tard, le bouton de contact enverra un message au photographe. Pour l'instant, seulement afficher le contenu des trois champs dans les logs de la console.

**Responsive design**
“Pour cette itération, pas besoin que le site soit responsive sur mobile.”

**Accessibilité**
Il est très important que notre site soit accessible aux utilisateurs malvoyants.  
Toutes nos photos doivent comporter des descriptions textuelles, et vous devez les inclure dans la page.  
De plus, l'utilisateur doit pouvoir utiliser les commandes du clavier pour naviguer sur le site, comme les touches fléchées de la lightbox"

- Utilisez des éléments HTML "sémantiques" qui décrivent leur intention autant que possible, au lieu de mettre des éléments `<div>` et `<span>` partout.
- Lorsque vous devez créer un élément personnalisé, ajoutez des attributs ARIA pour décrire ce qu'il fait.
- Le code devrait passer les tests AChecker sans “known issue” (afin qu'il soit conforme aux WCAG).
- Toute la gestion des événements (par exemple, les clics et les pressions au clavier) doit être configurée (utilisez KeyboardEvent.key ou KeyboardEvent.code.).
- Utilisez un lecteur d'écran gratuit pour vous faire une idée de ce que représente l'utilisation du site pour une personne malvoyante.

### <a id="2.2"> 2.2 - Contraintes techniques additionnelles</a>

- Le code est séparé en différents fichiers (HTML, CSS, JavaScript).
- ESLint est utilisé (avec les paramètres par défaut) pour garantir que le code est robuste. Ceci est particulièrement facile à intégrer avec l'IDE VSCode.
- Une version moderne (ES6 ou supérieure) de JavaScript est utilisée et les fonctionnalités obsolètes ne sont pas utilisées.
- Le code est lisible. Il faudra s'assurer que les variables et fonctions ont un nom qui ont un sens, et commenter le code lorsque le nom n'indique pas explicitement ce qu'il se passe.

### <a id="2.3">2.3 - Livrables</a>

- Un dépôt de code sur GitHub avec des fichiers HTML, CSS et JavaScript.
- Une version mise à jour du JSON (avec alt-text).

[:top: Retour à l'index](#index)

___

## <a id="3">3 - Etude de la maquette</a>

[Maquette Figma](https://www.figma.com/file/Q3yNeD7WTK9QHDldg9vaRl/UI-Design-FishEye-FR)

### <a id="3.1">3.1 - Page d'accueil</a>

Un header, un main, pas de footer.

**Header :** Un logo, un heading

**Main :** une galerie de photographes (grid CSS)

Un ``<article>`` ***photographe***, répliqué

- Une photo
- Un nom
- Une localisation (ville, pays)
- Une citation
- Un tarif journalier

### <a id="3.2">3.2 - Page photographe</a>

Un header, un main, pas de footer.

**Header :** un logo

**Main :**

- 1 ``<section>`` ***photographe*** (même composant que dans la page d'accueil)
- 1 bouton "Contactez-moi" qui ouvre une modale
- 1 `<section>` ***galerie***
- 1 `<select>` pour trier la galerie
- Des `<articles>` comprenant : 1 image, 1 titre, 1 compteur de like, 1 bouton like, 1 lien vers une modale
- 1 widget comprenant : 1 compteur du total des likes, 1 icône *like*, le tarif journalier

**Modale *Contactez-moi***

Un formulaire avec :

- 1 heading
- 4 `<input type="text>`
- 1 bouton *envoyer*
- 1 bouton *fermer*

**Modale *Lightbox***

- 1 image
- 1 titre
- 2 boutons de navigation
- 1 bouton *fermer*

[:top: Retour à l'index](#index)

___

## <a id="4">4 - Etude de la codebase originale</a>

### <a id="4.1">4.1 - HTML</a>

Page d'accueil - index.html

```html
<body>
    <header>
        <img>
        <h1>
    </header>
    <main>
        <div class="photographer_section">
    </main>

</body>

```

Page photographe - photographer.html

```html
<body>
    <header>
        <img>
    </header>
    <main>
        <div class="photograph-header">
            <button>
        </div>
    </main>
    <div id="contact-modal">
    <form>
</body>

```

### <a id="4.2">4.2 - CSS</a>

Toutes les pages HTML importent style.css

**photographer.css:**

- #contact_modal
- .photograph-header
- .contact_button
- .modal
- .modal header
- .modal header img
- .modal header h2
- form
- form label
- form div
- form input

**style.css:**

`@import photographer.css`

- Body
- Header
- h1
- .logo
- .photographer_section
- .photographer_section article
- .photographer_section article h2
- .photographer_section article img

### <a id="4.3">4.3 - JavaScript</a>

#### index.js

Appelle `init()`

```javascript

    async function getPhotographers() {
        const photographers = [
            {
                "name": "Ma data test",
                "id": 1,
                "city": "Paris",
                "country": "France",
                "tagline": "Ceci est ma data test",
                "price": 400,
                "portrait": "account.png"
            },
            {
                "name": "Autre data test",
                "id": 2,
                "city": "Londres",
                "country": "UK",
                "tagline": "Ceci est ma data test 2",
                "price": 500,
                "portrait": "account.png"
            },
        ]
        return ({
            photographers: [...photographers, ...photographers, ...photographers]})
    }
```

Récupère les données du JSON et retourne une liste de quelque chose (??)

```js

    async function displayData(photographers) {
        const photographersSection = document.querySelector(".photographer_section");

        photographers.forEach((photographer) => {
            const photographerModel = photographerFactory(photographer);
            const userCardDOM = photographerModel.getUserCardDOM();
            photographersSection.appendChild(userCardDOM);
        });
    };
}
```

- Ne retourne rien (modifie le DOM)
- Prend un argument `photographers` (liste générée par `getPhotographers()`)
- Récupère l'adresse de `.photographer_section` dans l'HTML.
- Crée une variable `photographerModal` dont la valeur est le résultat de `photographerFactory(photographer)`
- La valeur de cette variable a le format `{name, picture, getUserCardDOM()}`
- Ajoute un enfant dont la valeur est `userCardDOM` à `photographerSection`

```js
    async function init() {
            // Récupère les datas des photographes
            const { photographers } = await getPhotographers();
            displayData(photographers);
        };
```

- Crée un objet `photographers` qui contient les données des photographes
- = await ?
- Appelle la fonction `displayData(photographers)`

#### photographer.js

**/factories/photographer.js:**

```js
function photographerFactory(data) {
    const { name, portrait } = data;

    const picture = `assets/photographers/${portrait}`;

    function getUserCardDOM() {
        const article = document.createElement( 'article' );
        const img = document.createElement( 'img' );
        img.setAttribute("src", picture)
        const h2 = document.createElement( 'h2' );
        h2.textContent = name;
        article.appendChild(img);
        article.appendChild(h2);
        return (article);
    }
    return { name, picture, getUserCardDOM }
}
```

- photographerFactory prend 1 argument
- crée un objet avec deux keys {name, portrait} dont les valeurs respectives viennent de data
- possède une fonction getUserCardDOM()
- retourne un objet avec `{name, picture, le résultat de getUserCardDOM}`

La fonction getUserCardDom :

- Injecte un article dans le HTML
- Injecte une image dans le HTML
- Définit un attribut source à la balise `<img>` et une valeur = la valeur de la variable `picture`
- Injecte un h2
- Ajoute la valeur de la variable `name` en texte dans le h2
- Ajoute l'image et le h2 à l'article
- `return` l'article

#### /utils/contactForm.js

2 fonctions pour ouvrir et fermer la modale du formulaire.

### <a id="4.4">4.4 - JSON</a>

***photographers.json*** contient 2 objets :

- photographers, une liste de 6 objets
- media : une liste de 59 objets

```json
{
    "photographers": [
        {
            "name": "Mimi Keel",
            "id": 243,
            "city": "London",
            "country": "UK",
            "tagline": "Voir le beau dans le quotidien",
            "price": 400,
            "portrait": "MimiKeel.jpg"
        }
    ],
    "media": [
        {
            "id": 342550,
            "photographerId": 82,
            "title": "Fashion Yellow Beach",
            "image": "Fashion_Yellow_Beach.jpg",
            "likes": 62,
            "date": "2011-12-08",
            "price": 55
        }
    ]
}
```

### <a id="4.5">4.5 - Décomposition de la codebase</a>

1. init() appelle la fonction `getPhotographers()`

`getPhotographers()` lui renvoie un objet avec 1 clé `photographers` / 1 valeur (une liste) qui contient des objets.

```js
    {
    photographers : [
            {
                "name": "Ma data test",
                "id": 1,
                "city": "Paris",
                "country": "France",
                "tagline": "Ceci est ma data test",
                "price": 400,
                "portrait": "account.png"
            },
            {
                "name": "Autre data test",
                "id": 2,
                "city": "Londres",
                "country": "UK",
                "tagline": "Ceci est ma data test 2",
                "price": 500,
                "portrait": "account.png"
            },
        ]
    }
```

2. `init()` appelle `displayData(photographers)`
`displayData(photographers)` récupère l'élément du DOM dont la classe est `.photographer_section`
3. pour chaque élément de `photographers`, soit pour chaque objet de la liste `photographers`, elle initialise une constante `photographerModel` dont la valeur est `photographerFactory(photographer)` soit un objet avec 3 clés :

- `name` : la valeur de `name` est égale à celle de l'objet passé en argument de `photographerFactory()`  
- `picture`: la valeur de `picture` est égale à `assets/photographers/${portrait}`, `portrait` est récupéré dans l'objet passé en argument de `photographerFactory()`
 - La fonction `getUserCardDom`

4. `init()` initalise une constante `userCardDOM` qui est égale à ce que renvoie la méthode getUsersCardDOM appliquée sur photographerModel.

5. `getUserCardDOM()` :

- Initialise une constante pour préparer l'injection d'un `<article>` dans le DOM
- Initialise une constante pour préparer l'injection d'une `<img src="${picture}"`
- Initialise un h2 dont le contenu est celui de la valeur de `name`
- Joint à l'article l'image et le h2
- Retourne la valeur de `article`

5. `init()` joint à photographersSection la valeur retournée par userCardDOM soit

```js
{
const getUserCardDom =  document.createElement( 'article' )
                        document.createEment( 'img' )
                        img.setAttribute(src, 'assets/photographers/account.png')
                        document.createElement( 'h2' )
                        h2.textContent = 'Ma data test'
                        article.appendChild(img)
                        article.appendChild(h2)
                        return(article)
}
```

soit en HTML :

```html
<div class="photographer_section">
    <article>
        <img src="assets/photographers/account.png">
        <h2> Ma data test </h2>
    </article>
</div>
```

### Synthèse

1. `init()` appelle `getPhotographers()`
2. `getPhotographers()` récupère les données du JSON
3. `get Photographers()` retourne un objet `{photographers: []}`
4. `init()` stock le résultat dans un objet `{photographers}`
5. `init()` appelle `displayData()` et passe `{photographers}` en argument.

6. `displayData()` stock l'adresse de l'élément HTML `.photographer_section` dans `photographerSection`
7. `displayData()` passe chaque objet dans `photographerFactory()`
8. `photographerFactory()` retourne un objet `{name, picture, getUserCardDOM}`
9. `displayData()` stock l'objet dans `photographerModel`
10. `displayData()` appelle la méthode `.getUsercardDom` sur l'objet
11. `displayData()`stock la valeur renvoyée dans une constante `userCardDOM`
12. `displayData()` ajoute `userCardDOM` à `.photographer_section`

[Factory pattern](https://refactoring.guru/fr/design-patterns/factory-method)

[:rocket: Workflow - Whimsical](https://whimsical.com/p6-default-codebase-NmtiyYW4fcZdGe7scF4N9h)

[:top: Retour à l'index](#index)

___

## <a id="5">5 - Codebase existante VS résultat final</a>

### index.html
En l'état, la codebase existante permet de récupérer des données dans une constante "placeholder", des les transformer et d'injecter dans l'index HTML un ou plusieurs `<article>` comprenant :

- Une image
- un h2

Le résultat final attendu est de récupérer des données des photographes depuis un fichier JSON, de les transformer et d'injecter dans l'index HTML un ou plusieurs `<article>` comprenant :

- Une image
- un h2
- Une localisation
- Une citation
- Un tarif journalier

### photographer.html
En l'état, la codebase existante permet de créer un article pour 1 photographe (avec image et h2), mais il faudra modifier la fonction ou en créer une nouvelle. La fonction actuelle effectue une boucle à travers toute la liste des photographes pour créer leur article respectif, or nous n'avons besoin que des données que pour un photographe ici.

Le résultat final attendu est de :

**1.** Prévoir une `<section class="photographer_details">` dans l'HTML, prévoir une `<section class="gallery">`
**2.** récupérer les données d'un photographe spécifique depuis un fichier JSON et d'injecter dans la `<section class="photographer_details">` les éléments suivants :

à la section photographer_details :

- Une image
- Un titre h2
- Une localisation
- Une citation

au widget :

- Un tarif journalier

Note : il faudra leur attribuer des classes pour que le CSS puissent les placer et leur donner un style une fois dans la page.

**3.** Récupérer les données des photos et vidéos depuis un fichier JSON et ajouter :

à la `<section class="gallery">`

- Une image
- Un titre h3
- Un nombre de likes
- Une checkbox
- Une date (attribut de donnée ?)

au widget `<div class="widget">`

- Un nombre total de likes calculé depuis la somme des likes de toutes les photos/vidéos du photographe

[:top: Retour à l'index](#index)

___

## <a id="6">6 - Planification du projet</a>

1. GLOBAL | Répartir le CSS en SCSS
2. GLOBAL | Faire le design statique complet des 2 pages (+ 2 modales)
3. INDEX.HTML | Compléter les fonctions existantes pour générer des articles complets
4. GLOBAL | ajouter les champs Aria au JSON
5. PHOTOGRAPHERS.HTML | Créer les fonctions pour peupler la section "photographer_details"
6. PHOTOGRAPHERS.HTML | Créer une constante "placeholder" et les fonctions associées pour peupler la section "galerie"
7. INDEX.HTML | Remplacer les données "placeholder" par une fonction qui exploite le JSON
8. PHOTOGRAPHERS.HTML | Remplacer les données "placeholder" par une fonction qui exploite le JSON (details/galerie)
9. PHOTOGRAPHERS.HTML | Créer une fonction pour faire la somme des likes et une pour les retourner dans l'HTML
10. PHOTOGRAPHERS.HTML | MODALE | Implémenter les fonctions de validation du formulaire.
11. GLOBAL | Accessibilité : ajouter les key listeners pour la navigation au clavier

[:top: Retour à l'index](#index)

___

## <a id="Annexe1">Annexe 1 - Concepts à apprendre</a>

**Rest parameter, Spread operator:**

- [MDN | Paramètres du reste / Rest parameter](https://developer.mozilla.org/fr/docs/Web/JavaScript/Reference/Functions/rest_parameters)
- [MDN | Syntaxe de décomposition / Spread operator](https://developer.mozilla.org/fr/docs/Web/JavaScript/Reference/Operators/Spread_syntax)
- [Mindsers | Rest parameter et spread operator](https://mindsers.blog/fr/post/rest-parameter-et-spread-operator-en-javascript/)

**JS Promises, async, await:**

- [MDN | Faciliter la programmation asynchrone avec async et await](https://developer.mozilla.org/fr/docs/Learn/JavaScript/Asynchronous/Async_await)
- [MDN | Promise](https://developer.mozilla.org/fr/docs/Web/JavaScript/Reference/Global_Objects/Promise)
- [MDN | Asynchrone](https://developer.mozilla.org/fr/docs/Glossary/Asynchronous)
- [MDN | Async](https://developer.mozilla.org/fr/docs/Web/JavaScript/Reference/Statements/async_function)

**Destructuring objects**

- [What is the difference between const and const {} in JavaScript](https://stackoverflow.com/questions/41058569/what-is-the-difference-between-const-and-const-in-javascript)

**Design patterns:**

- [MDN | Factory pattern in JavaScript](https://www.dofactory.com/javascript/design-patterns/factory-method)

**CSS:**

- [MDN | CSS Grid](https://developer.mozilla.org/fr/docs/Web/CSS/grid)

[:top: Retour à l'index](#index)

## <a id="Annexe2">Annexe 2 - Questions mentorat</a>

- Promises / Sync/async
- Factory method
- variables dans l'URL
- 