# Introduction

L'objectif du document est la création d'une *cheat sheet* ou "feuille de triche". 

L'ensemble des fonctions que vous devez documenter se trouvent dans ce document, à vous de  remplir les espaces vides 😉

Ce document pourra vous suivre tout au long de vos études, n'hésitez à le compléter au fur et à mesure.

---

Pour compléter le document, vous utiliserez la fonction **fork** de GitHub pour copier ce projet dans votre espace personnel.

[Si besoin, rendez-vous dans ce dépôt pour revoir les bases de Javascript](https://github.com/Maxence-Machu/javascript-basic-memo)

---

## La fonction GetElementByID()

### Que fait la fonction ?
La méthode getElementById() renvoie un objet qui représente l'élément dont la propriété  id correspond à la chaîne de caractères spécifiée.
Étant donné que les ID d'élément doivent être uniques, s'ils sont spécifiés, ils constituent un moyen utile d'accéder rapidement à un élément spécifique.

### Pourquoi l'utiliser ?
La fonction getElementById doit être utilisée si l'on veut utiliser un élément du DOM en HTML grâce à Javascript 

#### Note supplémentaire
La fonction getElementByID est à ne pas confondre avec la fonction *getElementsByClassName*. 
Les ID dans une page web sont uniques, on ne peut donc pas récupérer plusieurs éléments avec cette fonction. 

### Exemple de code:
```javascript
let element = document.getElementByID('mon-element');
console.log(element);
```

## La fonction GetElementsByClassName()

### Que fait la fonction ?
Renvoie un objet de type tableau de tous les éléments enfants qui ont tous les noms de classe donnés.  Lorsqu'il est appelé sur l'objet document, le document complet est recherché, y compris le nœud racine.  

### Pourquoi l'utiliser ?
La méthode **`Element.getElementsByClassName()`**  retourne une [`HTMLCollection`]  contenant une référence sur tous les éléments ayant les noms de classes passés en paramètre. 

### Exemple de code:
```javascript
let element = document.getElementsByClassName('test')
console.log(test); 
```

## La fonction querySelector() et querySelectorAll()

### Que fait la fonction ?
La méthode  `querySelector()`  retourne un objet  `Element`  représentant le premier élément dans le document correspondant au sélecteur (ou au groupe de sélecteurs) CSS passé en argument ou la valeur  `null`  si aucun élément correspondant n’est trouvé.

La méthode  `querySelectorAll()`  renvoie un objet appartenant à l’interface  `NodeList`. Les objets  `NodeList`  sont des collections (des listes) de nœuds.

### Pourquoi l'utiliser ?
Permet de sélectionner une balise grâce à un sélecteur CSS.

### Exemple de code:
```javascript
document.querySelectorAll('BODY > TABLE .MaClass'); 
elementTable.querySelectorAll('.MaClass');
```

## La fonction addEventListener()

### Que fait la fonction ?
La méthode `**addEventListener()**` d'[`EventTarget`] installe une fonction à appeler chaque fois que l'événement spécifié est envoyé à la cible

### Pourquoi l'utiliser ?
La méthode `addEventListener()`  fonctionne en ajoutant une fonction, ou un objet implémentant  [`EventListener`]), à la liste des écouteurs d'évènements du type d'évènement spécifié dans la  [`EventTarget`] dans laquelle il est appelé.

### Exemple de code:
```javascript

var btn = document.querySelector('button');

function random(number) {
  return Math.floor(Math.random()*(number+1));
}

btn.onclick = function() {
  var rndCol = 'rgb(' + random(255) + ',' + random(255) + ',' + random(255) + ')';
  document.body.style.backgroundColor = rndCol;
}
```

## La fonction stopPropagation()

### Que fait la fonction ?
Cette méthode va stopper la propagation d'un évènement après qu'un gestionnaire d'évènement (gérant l'évènement en question) ait été atteint.

### Pourquoi l'utiliser ?
Pour stopper la propagation d'un événement afin de ne pas atteindre le reste du code.

### Exemple de code:
```javascript
$(function() {

$('#soumettre').click(function ( event ) {

if (!validerDonnees()) {

event.preventDefault();

event.stopPropagation();  // n'exécutera pas ce qu'il y a dans
$('p.surbrillance').click()
}
});
});
```

## La fonction addEventListener('mousemove', maFonction)

### Que fait la fonction ?
L'évènement `mousemove` est déclenché à partir d'un élément lorsqu'un dispositif de pointage (ex. une souris) est déplacé lorsque le curseur est à l'intérieur de l'élément.

### Pourquoi l'utiliser ?
Créer une zone de déplacement du curseur.

### Exemple de code:
```javascript
// Un booléen qui, lorsqu'il est vrai, indique que le déplacement de
// la souris entraîne un dessin sur le canevas
let isDrawing = false;
let x = 0;
let y = 0;

const myPics = document.getElementById('myPics');
const context = myPics.getContext('2d');

// On récupère le décalage du canevas en x et y par rapport aux bords
// de la page
const rect = myPics.getBoundingClientRect();

// On ajoute les gestionnaires d'évènements pour mousedown, mousemove
// et mouseup
myPics.addEventListener('mousedown', e => {
  x = e.clientX - rect.left;
  y = e.clientY - rect.top;
  isDrawing = true;
});

myPics.addEventListener('mousemove', e => {
  if (isDrawing === true) {
    drawLine(context, x, y, e.clientX - rect.left, e.clientY - rect.top);
    x = e.clientX - rect.left;
    y = e.clientY - rect.top;
  }
});

window.addEventListener('mouseup', e => {
  if (isDrawing === true) {
    drawLine(context, x, y, e.clientX - rect.left, e.clientY - rect.top);
    x = 0;
    y = 0;
    isDrawing = false;
  }
});

function drawLine(context, x1, y1, x2, y2) {
  context.beginPath();
  context.strokeStyle = 'black';
  context.lineWidth = 1;
  context.moveTo(x1, y1);
  context.lineTo(x2, y2);
  context.stroke();
  context.closePath();
}
```

## La fonction parseInt()

### Que fait la fonction ?
Convertit une chaîne de caractères en nombre entier.

### Pourquoi l'utiliser ?
Permet de définir la base de conversion.

### Exemple de code:
```javascript
1.  // sans parseInt()
2.  let saisie=  "3";
3.  document.write(saisie+6);
```


## La variable "event" dans le code suivant:

### Code:
```javascript
element.addEventListener('event-name', function(event) {
  console.log(event);
});
```

### Qu'est-ce que cette variable ?
La variable Event va servir à lister tous les event classés par nom.

### Pourquoi l'utiliser ?
Pour s'organiser et être plus rapide et efficace 

