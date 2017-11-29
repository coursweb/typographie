---
layout: page
title: Webfonts
permalink: /typo/webfonts/
---

## CSS3 et Webfonts

Depuis les débuts du web, la palette typographique à disposition des designers était limitée à une poignée de fontes (Arial, Verdana, Georgia, Times, Courier...), disponibles sur la grande majorité des systèmes d'exploitation.

Méthode classique: le "fontstack". 

Exemple, pour déclarer une fonte: 

```css
body {
   font-family: "HelveticaNeue-Light", "Helvetica Neue Light", "Helvetica Neue", 
   Helvetica, Arial, "Lucida Grande", sans-serif; 
   font-weight: 300;
}
```

Entre 2008 et 2010, tous les navigateurs ont implémenté le **CSS3 Fonts Module**, permettant de charger des fontes spécifiées par les styles CSS avec la propriété *@font-face*.


### @Fontface

La syntaxe @font-face, optimisée (c'est la version proposée par FontSquirrel):

```css
@font-face {
    font-family: 'univers';
    src: url('univers.eot');
    src: url('univers.eot?#iefix') format('embedded-opentype'),
         url('univers.woff2') format('woff2'),
         url('univers.woff') format('woff'),
         url('univers.ttf') format('truetype');
    font-weight: normal;
    font-style: normal;
}
```

On notera que les fontes sont proposées dans quatre formats: eot, woff2, woff, ttf.

- **eot** : format utilisé par Microsoft (Internet Explorer)
- **ttf**
- **woff** : format compressé
- **woff2** : format compressé

Le support des navigateurs pour les formats woff et woff2 ayant fait des progrès, [le site css-tricks](https://css-tricks.com/snippets/css/using-font-face/) propose en 2016 d'utiliser la syntaxe suivante:

```css
@font-face {
  font-family: 'MyWebFont';
  src: url('myfont.woff2') format('woff2'),
       url('myfont.woff') format('woff'),
       url('myfont.ttf') format('truetype');
}
```

### Google Fonts

Depuis 2010, Google Fonts est un service d'hébergement gratuit de fontes pour le Web. Ces polices sont sous licences libres. Ceci nous permet d'inclure très rapidement une police dans le code. De plus, les fontes sont rangées par classifications. Elles sont affichées avec un lien de téléchargement, ce qui permet de les obtenir dans plusieurs formats tels que TrueType ou OpenType.

![Goodgle Fonts, une sélection de fontes Google par Frank Adebiaye.](/cours-typographie/img/goodgle-fonts.png)

Inclure une fonte Google dans son code:

Le fonctionnement est simple. Il suffit de choisir une police parmi la liste. Ensuite, en cliquant sur *Use this font*, on nous demande de suivre les instructions plus bas dans le menu. Ceci générera un lien à copier-coller dans le head de notre HTML et d'utiliser le nom de la typographie dans le CSS.
