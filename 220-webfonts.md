---
layout: page
title: Webfonts
permalink: /typo/webfonts/
---

## CSS3 et Webfonts

Depuis les débuts du web, la palette typographique à disposition des designers était limitée à une poignée de fontes (
<span style="font-family: Arial">Arial</span>, 
<span style="font-family: Verdana">Verdana</span>, 
<span style="font-family: Georgia">Georgia</span>, 
<span style="font-family: Times">Times</span>, 
<span style="font-family: Courier">Courier</span>...), disponibles sur la grande majorité des systèmes d'exploitation.

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

On notera que dans ce code, les fontes sont proposées dans quatre différents formats: eot, woff2, woff, ttf.

- **eot** : format utilisé par Microsoft (Internet Explorer)
- **ttf** : True Type Font, format aussi utilisé pour l'impression
- **woff** : format compressé, conçu pour le web
- **woff2** : format compressé, amélioration du format woff2

Le support des navigateurs pour les formats woff et woff2 ayant fait des progrès, [le site css-tricks](https://css-tricks.com/snippets/css/using-font-face/) propose en 2016 d'utiliser la syntaxe suivante:

```css
@font-face {
  font-family: 'MyWebFont';
  src: url('myfont.woff2') format('woff2'),
       url('myfont.woff') format('woff'),
       url('myfont.ttf') format('truetype');
}
```

### Kerning, ligatures, etc

Voir l'excellent guide de Grilli Type:

[https://github.com/grillitype/web-fonts-guide](https://github.com/grillitype/web-fonts-guide)

