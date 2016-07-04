class: center, middle

# Formation : Outils pour front dev

---

# Build ton style

1. Préprocesseurs
2. Post-processeurs
3. Methodes et rêgles

---

# Les préprocesseurs

Le web se build depuis 2015.
Pour les css on utilise les préprocesseurs.
* Sass
* Stylus
* Less

En entré on a donc des fichiers `.sass` `.scss` `.less` ou `.styl`
et en sortie un fichier `.css` respectant les standrards du W3C.

---

# Pourquoi ?

* Faciliter l’écriture du css.
* Eviter des calculs humain.
* Factoriser son code.

--

Et pour tout ça :
--

* variables

--

* fonctions

--

* mixins (permettant de réaliser des sorties CSS paramétrables)

--

* inclusion de partial

--

* nesting (imbrications des sélecteurs pour éviter la répétition)

--

* optimisation et abstraction poussée (via les mixins, placeholders et @extend)

--

Pause exercice :
Tous sur ce codepen [codepen.io/ryuran/pen/mEwyrq](http://codepen.io/ryuran/pen/mEwyrq/?editors=1100)

---

# Exercice

1. Faire un fork et choisissez un préprocesseur

--

3. Créer 2 variables de couleur
4. Utilisez une variable pour le `background-color` de la `<section>`
5. Et une pour la couleur de texte

--

6. Utiliser une fonction pour définir une couleur de text plus claire/foncée
pour les `<p>` se trouvant dans un `<section>` (darken, lighten)
   
--

7. Mettre les items de la list sur une seule ligne avec une marge à gauche de chacune
8. Sauf le premier item (à l'aide du nesting et `:first-child`)

--

9. Faire une mixin qui défini un bord de 2px pixels et la couleur de text avec la couleur passé en paramètre
10. Appliquer la aux `<li>` avec la couleur de votre choix
11. Et au titre `<h1>` avec une autre couleur


---

# Post-processeurs

Rappel : l'idée du préprocesseur est de généré du css standard

Mais les standards ça évolue et donc ce n'est pas forcement bien supporté.

Par exemple l'unité de mesure `rem` n'est pas supporté par IE8.

Notre préprocesseur générera ceci :
```css
h1 {
	fontsize: 2rem;
}
```

Il existe un plugin de PostCSS, __pixrem__ qui ajoute un fallback en `px`.

Et donc en sortie on aura ceci :
```css
h1 {
	fontsize: 32px;
	fontsize: 2rem;
}
```

---

# Autoprefixer

Est un plugin PostCSS.

Il ajoute les préfixe navigateur necessaire pour le scope navigateur du projet.

--

En se basant sur les données de [caniuse.com](http://caniuse.com/)

--

Et sur des stats d’utilisation des navigateur.

--

Déléguer ce travail à autoprefixer permet de s’assurer
que le code source du projet ne soit pas polué de préfixes
potentielement inutiles dans un futur proche.

---

# Autoprefixer

```css
::placeholder {
  color: red;
}
```
Donnera :
```css
::-webkit-input-placeholder {
  color: red;
}
::-moz-placeholder {
  color: red;
}
:-ms-input-placeholder {
  color: red;
}
::placeholder {
  color: red;
}
```

---

# Un grand pouvoir implique de grandes responsabilités

Cette complexification du code et cette facilité à générer du code complexe
implique un bon encadrement.

Il ne faut pas oublier que le navigateur web interprète le css et donc le dev
en est responsable.

Faire une boucle sass qui génère 50000 class c’est facile mais coté navigateur
c’est lourd. [codepen.io/ryuran/pen/JKJdbr][http://codepen.io/ryuran/pen/JKJdbr/?editors=0100]

---

# Les rêgles du diable

> Les ID c'est le mal

> Le nesting c'est le mal

> !important c'est le mal

> La magie c'est le mal

> Je prefère 2 espaces qu’une tabulation pour indenter le code

---

# Linter FTW (For The Win)

Un linter c'est un outils qui permet de controler que le code respecte certaine
rêgles.

Il existe des linter pour la plus part des langage.

Plus le language est permissif plus le linter est important afin que
tout le monde écrive son code de la même manière
```css
.foo{color:red}
```
```css
.foo {
  color: red;
}
```
```css
.foo
{
    color : red ;
}
```
Ces 3 écritures fonctionnent en scss mais c'est désagréable de voir ça
dans un même code.

---

# Des trucs à lire

* [Preprocesseurs](http://putaindecode.io/fr/articles/css/preprocesseurs/)
* [Post-processeurs](http://putaindecode.io/fr/articles/css/preprocesseurs/post-processeurs/)
