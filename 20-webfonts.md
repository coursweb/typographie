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

La syntaxe @font-face fonctionne de la manière suivante:

```css
@font-face {
  font-family: 'Univers';
  src: url(univers-regular.woff);
}
```

Cette déclaration permet de charger la fonte, il faut ensuite l'appliquer. Par exemple comme ceci:

body {
  font-family: 'Univers', sans-serif;
}

#### Familles de fontes

Quand on souhaite utiliser plusieurs variantes – par exemple Univers en *55 Roman* et *65 Bold* – on peut les déclarer comme une même famille:

@font-face {
    font-family: 'Univers';
    src: url(univers-55-roman.woff);
    font-weight: normal;
}

@font-face {
    font-family: 'Univers';
    src: url(univers-65-bold.woff);
    font-weight: bold;
}

#### Charger plusieurs formats

Un problème rencontré lors de l'utilisation de webfonts est que les divers navigateurs utilisent des formats de fontes différents.

Voici une liste de formats possibles:

- **ttf** : True Type Font, format aussi utilisé pour l'impression
- **otf** : Open Type Font, format aussi utilisé pour l'impression
- **eot** : format compressé utilisé par Microsoft (Internet Explorer)
- **woff** : format compressé, conçu pour le web
- **woff2** : format compressé, amélioration du format woff2

Le format WOFF est un nouveau format développé pour le web. Il s'agit de fichiers OTF compressés afin de charger plus rapidement.

Le support des navigateurs pour les formats woff et woff2 ayant fait des progrès, [le site css-tricks](https://css-tricks.com/snippets/css/using-font-face/) propose en 2016 d'utiliser la syntaxe suivante:

```css
@font-face {
  font-family: 'MyWebFont';
  src: url('myfont.woff2') format('woff2'),
       url('myfont.woff') format('woff'),
       url('myfont.ttf') format('truetype');
}
```

La même syntaxe [est préconisée par Bram Stein](http://alistapart.com/article/using-webfonts) sur A List Apart en 2017.

Dans la période intiale des webfonts, entre 2011 - 2016, des syntaxes plus compliquées étaient utilisées, ajoutant d'autres formats comme SVG (pour appareils iOS) et EOT (pour Internet Explorer). Ces formats ne sont désormais plus nécessaires.

### Kerning, ligatures, etc

Voir l'excellent guide de Grilli Type:

[https://github.com/grillitype/web-fonts-guide](https://github.com/grillitype/web-fonts-guide)

