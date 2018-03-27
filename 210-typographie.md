---
layout: page
title: Typographie
permalink: /typo/
---

![Emil Ruder: Typographie (1967)](/cours-typographie/img/emil-ruder-typographie-800px.jpg)

Depuis les débuts du web, la typographie a été l'un des aspects les plus importants – le web étant constitué à ses débuts uniquement de texte.

Des les premières versions du CSS, des propriétés sont introduites afin de pouvoir exercer un contrôle sur la typographie.

Voici les principales propriétés CSS spécifiques à la typographie:

* **font-family** : Permet de spécifier la police.
* **font-size** : Permet de spécifier la taille de la police. On peut utiliser des unités absolues ou relatives.
* **font-style** : Permet de spécifier un style (*italic* ou *oblique*).
* **font-weight** : Permet de spécifier la graisse, avec un mot-clé (*normal*, *bold*) ou avec une valeur numérique allant de 100 à 900 (voir ci-dessous).
* **font-variant** : Permet de spécifier des petites majuscules, avec la valeur "small-caps".

Liste des équivalences des valeurs numériques du `font-weight`:

* 100 - équivalent à *Ultra-light* ou *Thin*
* 200 - équivalent à *Light* ou *Extra-Light*
* 300 - équivalent à *Book* ou *Light*
* **400** - équivalent à *Normal* (ou *Roman*, *Regular*), c'est la valeur par défaut
* 500 - équivalent à *Medium*
* 600 - équivalent à *Semi-Bold* 
* **700** - équivalent à *Bold* (gras)
* 800 - équivalent à *Extra-Bold* ou *Black*
* 900 - équivalent à *Ultra-Bold* ou *Extra-Black*

Pour que ces variantes soient visibles, il faut que la fonte les supporte. De nombreuses fontes ne proposent que les versions *normal* et *bold*. D'autres offrent plus d'options: *Univers* propose 5 versions (*45 Light, 55 Roman, 65 Bold, 75 Black, 85 Extra Black*), *Helvetica Neue* en comporte 8 (*Ultra-Light, Thin, Light, Normal, Medium, Bold, Heavy, Black*). 

Voici quelques fontes qui proposent toutes les 9 variantes supportées par le CSS: [Exo](https://fonts.google.com/specimen/Exo), [Libre Franklin](https://github.com/impallari/Libre-Franklin), ou [Raleway](https://github.com/impallari/Raleway).

![Tailles CSS dans Exo, Libre Franklin, Raleway](/cours-css/img/CSS-font-weight.png)

Autres propriétés:

* **line-height** : la hauteur de ligne 
* **text-transform** : permet de forcer les majuscules ou minuscules.
* **text-decoration** : permet d'appliquer un soulignement.
* **font-stretch** : permet de spécifier l'utilisation d'une fonte *condensed*, *semi-condensed*, *ultra-condensed* etc.

## Réglages typographiques avancés

- **text-align** (left, right, center, justify) : alignement
- **text-indent** : retrait de la première ligne d'un paragraphe
- **word-spacing** : espacement entre les mots
- **letter-spacing** : espacement des caractères
- **vertical-align** : alignement sur la ligne de base. Cf. [The vertical-align Property](https://bitsofco.de/the-vertical-align-property/), par Ire Aderinokun.

### Retrait

Pour un retrait de la première ligne, utiliser le code suivant:

```css
p { text-indent: 1.8em }
```

Pour ajouter une lettrine ("drop cap" en anglais) au début d'un paragraphe:

```css
p::first-letter {
  font-size: 200%;
  float: left;
}
```

