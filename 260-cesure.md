---
layout: page
title: Césure
permalink: /typo/cesure/
---

## Hyphenation, césure

### La propriété "hyphens"

Les navigateurs Firefox, Safari et IE10 supportent la césure (en anglais, *hyphenation*) depuis 2012. Actuellement (fin 2016) Chrome est en voie de l'implémenter.

Exemple de code fonctionnel en 2016:

```css
article p {
  word-break: break-word; /* solution de contournement pour Chrome */
  -webkit-hyphens: auto;
  -moz-hyphens: auto;
  -ms-hyphens: auto;
  hyphens: auto;
}
```

Les valeurs possibles sont: 

- `none` : pas de césure.
- `auto` : le navigateur applique la césure, en utilisant un dictionnaire de césure (fourni par le système d'exploitation). Pour que cela fonctionne, l'attribut `lang` doit être renseigné (normalement sur la balise html). 
- `manual` : la césure est uniquement appliquée si des caractères de césure sont présents, càd des tirets visibles, ou des tirets invisibles (*soft hyphen*, rendu par le code html `&shy;`).

Lire:  
[La gestion de la césure en CSS](http://openweb.eu.org/articles/la-gestion-de-la-cesure-en-css), par Nicolas Hoffmann, 2013.
