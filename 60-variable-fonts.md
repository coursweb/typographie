---
layout: page
title: Fontes Variables
permalink: fontes-variables.html
---

> Version 1.8 of the OpenType font format specification introduces an extensive new technology, affecting almost every area of the format. An **OpenType variable font** is one in which the equivalent of multiple individual fonts can be compactly packaged within a single font file. This is done by defining variations within the font, which constitute a single- or multi-axis design space within which many font instances can be interpolated. 

- [*Introducing OpenType Variable Fonts*](https://medium.com/variable-fonts/https-medium-com-tiro-introducing-opentype-variable-fonts-12ba6cd2369), par John Hudson, 2016


## Références

* [https://variablefonts.io/](https://variablefonts.io/) - A Variable Fonts Primer
* [https://www.axis-praxis.org/](https://www.axis-praxis.org/)
* [https://web.dev/variable-fonts/](https://web.dev/variable-fonts/)
* [Variable Fonts Are Here to Stay](https://design.google/library/variable-fonts-are-here-to-stay/), By Dave Crossland and Laurence Penney (Google Design)

Listes de fontes:

* [https://v-fonts.com/](https://v-fonts.com/) : un site listant des Variable Fonts disponibles.
* [Google Fonts catalog](https://fonts.google.com/?vfonly=true) (filter: variable fonts)
*  [Google Fonts axes values table](https://fonts.google.com/variablefonts) : liste des fontes variables sur Google Fonts, avec leurs paramètres (axes).

Outils web pour inspecter des Variable Fonts:

* [https://wakamaifondue.com/](https://wakamaifondue.com/) : outil web pour inspecter une fonte variable.
* [Samsa](https://lorp.github.io/samsa/src/samsa-gui.html) :  interactively visualizes the mechanics of variable fonts in innovative ways

La spécification CSS actuelle, CSS Fonts Module Level 4:

* Sur le site CSS Working Group: [https://drafts.csswg.org/css-fonts-4/](https://drafts.csswg.org/css-fonts-4/)


## Les axes des fontes variables

Selon la spécification OpenType Font Variations, qui a standardisé les fontes variables, il existe cinq axes standard:

- **Weight `<wght>`** : "Adjust the style from lighter to bolder in typographic color, by varying stroke weights, spacing and kerning, and other aspects of the type." Norme: "a value of 100 is thin, 400 is regular, 800 is extra bold"
- **Width `<wdth>`** : "Adjust the style from narrower to wider, by varying the proportions of counters, strokes, spacing and kerning, and other aspects of the type. This typically changes the typographic color in a subtle way, and so may be used in conjunction with Width and Grade axes." Norme: "100 is normal width, 200 is double-width, 50 is half-width"
- **Italic `<ital>`** : "Adjust the style from roman to italic. This can be provided as a continuous range within a single font file, like most axes, or as a toggle between two roman and italic files that form a family as a pair." Norme: "0 means roman letters and 1 means italic forms".
- **Slant `<slnt>`** : "Adjust the style from upright to slanted, also known to typographers as an 'oblique' style." Norme: "the value sets the slant angle in degrees".
- **Optical size `<opsz>`** : "Adapt the style to specific text sizes. At smaller sizes, letters typically become optimized for more legibility. At larger sizes, optimized for headlines, with more extreme weights and widths." Norme: "the value sets a point size that the design can respond to".


Ce sont les cinq axes définis dans la spécification OpenType. Selon TypeNetwork: "No other registered axes exists, i.e. axes definitions written into the specification of Opentype 1.8, but variable fonts can contain numerous  custom (unregistered) axes, for variation of styles that are new or unfamiliar to users."

[Dave Crossland](https://design.google/library/variable-fonts-are-here-to-stay/) (Google Fonts) donne quelques exemples : "A font can have its own axes beyond those 5 to customize any other elements, like x-height, serif style, stroke contrast, and vertical alignment."

Exemples d'axes originaux:

- **Recursive**, comporte un axe "Casual" (CASL). "Recursive uses its Casual axis to offer a range of personality, allowing you to get just the right tone for any context ... from a sturdy, rational Linear to a friendly, energetic Casual".
- **Fraunces**, comporte un axe "Wonky" (WONK). "The Wonk axis controls the substitution of “wonky” characters".

![Axes de la fonte *Recursive*](img/variable/recursive-axes.jpg)

### La propriété Optical Size

Explication de la "Optical Size": il s'agit de modifications des formes de la lettre, en fonction de la taille d'affichage. Cela existait déjà à l'époque de la typographie en plomb.

L'image ci-dessous montre les différentes tailles (de 72pts à 4pts) d'une fonte créée en 1894 (Century Expanded). Les petites tailles (à droite) ont été agrandies pour une meilleure comparaison.

![Axes de la fonte *Recursive*](img/variable/Century_Expanded-a-normalized.jpeg)

Selon Dave Crossland : "This tells browsers to control the optical size axis automatically — styles for headings, paragraphs, and captions all perfectly tuned, all from the same font."

Cette valeur est pensée pour correspondre à un taille de fontes en pixels, et garantir la meilleure lisibilité. Donc pour une fonte affichée en taille de 14 pixels, on règle opsz à 14 pour un rendu optimisé. Selon les fontes, les valeurs peuvent aller de 7 à 72 (pour *Literata*), ou de 8 à 144 (pour *Roboto Flex*). 

La propriété CSS `font-optical-sizing` possède seulement deux options: `auto` et `none`. Le réglage par défaut est "auto".

Quand une fonte variable possède un axe "opsz", le rendu sera donc automatique (s'adaptant à la taille de la fonte).

L'unique fonction de la propriété `font-optical-sizing` est de désactiver cet ajustement automatique (en choisissant "none").

```css
h1 {
  font-optical-sizing: none;
}
```

Il est aussi possible de forcer une valeur numérique (différente de celle choisie automatiquement), en utilisant les `font-variation-settings`, comme ci-dessous.

```css
h1 {
  font-size: 3rem;
  font-variation-settings: "opsz" 8;
}
```

### La propriété CSS `font-variation-settings`

La [spécification CSS indique](https://drafts.csswg.org/css-fonts-4/#font-variation-settings-def): 

This property provides low-level control over OpenType or TrueType font variations. It is intended as a way of providing access to font variations that are not widely used but are needed for a particular use case.

Exemple: 

```css
h1 {
  font-variation-settings: "BLDA" 0, "BLDB" 0, "SKLA" 0, "SKLB" 0, "SKLD" 0, "TRMA" 0, "TRMB" 973, "TRMC" 0, "TRMD" 0, "TRME" 0, "TRMF" 0, "TRMG" 0, "TRMK" 0, "TRML" 0, "WMX2" 12, "opsz" 102;
}
```

Précisions de la spécification:

When possible, authors should generally use the other properties related to font variations (such as `font-optical-sizing`), and only use this property for special cases where its use is the only way of accessing a particular infrequently used font variation.

For example, it is preferable to use `font-weight: 700` rather than `font-variation-settings: "wght" 700`.


## Charger une Variable Font depuis Google Fonts

Explications sur les URL Google Fonts: 

[https://developers.google.com/fonts/docs/css2#forming_api_urls](https://developers.google.com/fonts/docs/css2#forming_api_urls)


## Codepens de démonstration:

"Recursive Mono &amp; Sans, all axes from Google Fonts API", un codepen par Dave Crossland (Google Fonts):

<p class="codepen" data-height="300" data-default-tab="css,result" data-slug-hash="eYRJeqp" data-user="davelab6" style="height: 300px; box-sizing: border-box; display: flex; align-items: center; justify-content: center; border: 2px solid; margin: 1em 0; padding: 1em;">
  <span>See the Pen <a href="https://codepen.io/davelab6/pen/eYRJeqp">
  Recursive Mono &amp; Sans, all axes from Google Fonts API</a> by Dave Crossland (<a href="https://codepen.io/davelab6">@davelab6</a>)
  on <a href="https://codepen.io">CodePen</a>.</span>
</p>

---

"Simple weight slider for Hepta Slab", par Laurence Penney :

<p class="codepen" data-height="300" data-default-tab="result" data-slug-hash="ZEbqGYG" data-user="lorp" style="height: 300px; box-sizing: border-box; display: flex; align-items: center; justify-content: center; border: 2px solid; margin: 1em 0; padding: 1em;">
  <span>See the Pen <a href="https://codepen.io/lorp/pen/ZEbqGYG">
  Simple weight slider for Hepta Slab</a> by Laurence Penney (<a href="https://codepen.io/lorp">@lorp</a>)
  on <a href="https://codepen.io">CodePen</a>.</span>
</p>

---

"Optical size for CSS authors", par Laurence Penney

<p class="codepen" data-height="300" data-default-tab="result" data-slug-hash="GXQmmZ" data-user="lorp" style="height: 300px; box-sizing: border-box; display: flex; align-items: center; justify-content: center; border: 2px solid; margin: 1em 0; padding: 1em;">
  <span>See the Pen <a href="https://codepen.io/lorp/pen/GXQmmZ">
  Optical size for CSS authors</a> by Laurence Penney (<a href="https://codepen.io/lorp">@lorp</a>)
  on <a href="https://codepen.io">CodePen</a>.</span>
</p>

---

Une animation d'une Variable Font, en simple CSS:

<p class="codepen" data-height="300" data-default-tab="result" data-slug-hash="ZEoGxMw" data-user="eracom" style="height: 300px; box-sizing: border-box; display: flex; align-items: center; justify-content: center; border: 2px solid; margin: 1em 0; padding: 1em;">
  <span>See the Pen <a href="https://codepen.io/eracom/pen/ZEoGxMw">
  Variable font animation (Roboto)</a> by Manuel Schmalstieg (<a href="https://codepen.io/eracom">@eracom</a>)
  on <a href="https://codepen.io">CodePen</a>.</span>
</p>

---

"Hepta Slab Wave Animation", par Dave Crossland:

<p class="codepen" data-height="300" data-default-tab="result" data-slug-hash="QWEJpWa" data-user="davelab6" style="height: 300px; box-sizing: border-box; display: flex; align-items: center; justify-content: center; border: 2px solid; margin: 1em 0; padding: 1em;">
  <span>See the Pen <a href="https://codepen.io/davelab6/pen/QWEJpWa">
  Hepta Slab Wave Animation</a> by Dave Crossland (<a href="https://codepen.io/davelab6">@davelab6</a>)
  on <a href="https://codepen.io">CodePen</a>.</span>
</p>

---

## Autres références

Long article sur la perfomance des fontes variables:

[https://blog.logrocket.com/variable-fonts-is-the-performance-trade-off-worth-it/](https://blog.logrocket.com/variable-fonts-is-the-performance-trade-off-worth-it/)

Pages de démonstration de fontes variables:

- [Piazzolla](https://piazzolla.huertatipografica.com/)
- [Fraunces](https://fraunces.undercase.xyz/)
- [Recursive](https://www.recursive.design/)

