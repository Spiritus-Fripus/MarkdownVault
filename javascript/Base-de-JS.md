# JS

## Pourquoi javascript

**Interprété ou compilé à la volée par le navigateur**

**Language le plus populaire du moment**

- web moderne et dynamique
- accessible\*\*
- trés permissif
- synchrone/asynchrone

**Sa force**

- Modifier dynamiquement les éléments dans le DOM: Document Object Model
- Le Dom

[Stack overflow](https://survey.stackoverflow.co/2023/#technology-most-popular-technologies)

**Et maintenant ?**

JavaScript pour développer sur bureau,mobile,tabkette,React, Angular2+, Vue, etc.
Possibilité de développer des applications serveurs.
Nodejs, Deno, Express, Meteor, etc.

[State of JS](https://2020.stateofjs.com/en-US/)

**Domaine d'utilisation**

- IoT
- Système embarqués
- Applications Desktop
- Web
- Jeux-vidéo
- Mobile
- ML

**ECMAScript**

ECMAScript met à jour son language régulierement.

- ES6 = ES2015\*\*
- ES12 = ES2021\*\*

## Les variables

_mot clé_ **nom de la variable** "=", opérateur d'affectatuion

```JS
var jeSuisUneVariable = "variable globale"; // variable globale

function uneFonction() {
    let jeSuisUneVariable = 1;
// une var peut être redéclarée
// ici elle sera locale
    console.log(jeSuisUneVariable);
}

uneFonction();
console.log(jeSuisUneVariable);

function anyFunction() {
    let uneVariable = 'BIM';
    try {
        uneVariable = 'BAM';
    } catch (e) {
        console.error(e); // pas d'erreur , réaffectation
    }
    console.log(uneVariable); // BAM
}

anyFunction();
if (true) {
    let variableDansScopeIf = 'BOOM';
    console.log(variableDansScopeIf); // OUI

}
console.log(variableDansScopeIf); // ERROR car en dehors du scope
```

**const** et **let** sont apparues depuis ES6

```JS
let msg = "OUT";
console.log(msg); // OUT
function greet() {
    msg = "In";
    console.log(msg);
}

console.log(msg);
greet();
console.log(msg);
```

```JS
let msg = "Out";
console.log(msg);

function greet() {
    msg = "In";
    const msg2 = "Const In";
    console.log(msg + msg2);
}

console.log(msg);
greet();
console.log(msg + msg2);
```

## Les types

- **string**
- **number**
- **boolean**
- null => rien
- **Undefined => non défini**
- symbol (ES6)
- BigInt (>2^53) (ES6)
- **Object**

## Opérateur de comparaison

En javascript, les égalités sont pas farfois étonnantes, ceci vient principalement de la coercion

```JS
console.log("1 == \"1\"", 1 == "1"); // true
console.log("1 === \"1\"", 1 === "1"); // false
console.log("1 === 1", 1 === 1); // true
console.log("{} === {}", {} === {}); // false ???
console.log("[] === []", [] === []); // false
console.log("[] == ! []", [] == ![]); // true ???
console.log(" [] == []", [] == []); // false
```

## Concaténation

```JS
const prefix = "En jS , la concaténation prend se fait ";
const suffix = "avec le signe +, qui est aussi l'opérateur d'addition";

const preSuffix = prefix + suffix;
console.log(preSuffix);
console.log(prefix + "\"" + suffix)

// en ES6 , on a corrigé ca avec ` et ${}
console.log(`${preffix}${suffix}`);
console.log(`${prefix} entre " " les deux ${suffix}`);
```

## Structure de contrôle

```JS
const min = 3;
const max = 99;

if (min > max) {
    console.log("error");
} else if (min === max) {
    console.log("equal")
} else {
    console.log("looks great");
}
```

Dans un contexte booléen if(monTest) toute valeur en hs est évaluée à true en dehors de

- false
- 0
- ""
- null
- undefined
- NaN => Not a Number

```JS
const min = 3;
const max = 99;

switch (min < max) {
    case false:
        switch (min === max) {
            case true :
                console.log("equal")
                break;
            default:
                console.log("error");
        }
        break;
    default: // comme un else final
        console.log("looks great")
}
```

Exemple de switch simple:

```JS
const expr = 'Papayas';
switch (expr) {
    case 'Oranges':
        console.log('Oranges are $0.59 a pound.');
        break;
    case 'Mangoes':
    case 'Papayas':
        console.log('Mangoes and papayas are $2.79 a pound.');
        // Expected output: "Mangoes and papayas are $2.79 a pound."
        break;
    default:
        console.log(`Sorry, we are out of ${expr}.`);
}
```

## Les boucles

```JS
// for let x= ..., condition d'arrêt , incrémentation ou décrémentation {//code}

const classMatesNumber = 31;
for (let i = 0; i < classMatesNumber; i++) {
    console.log("Elève " + i);
    // console.log(`Elève ${i}`);
}

// ES6
// Mot clé / keyword
// for (const value of values {// code}
// for (const keyOfValue in values) {// code}
console.log("=== for of");
for (const number of arrayOfNumbers) {
    console.log(number);
}
console.log("=== for in");
for (const key in arrayOfNumbers) {
    console.log(arrayOfNumbers[key]);
}
```

```JS
const classMateNumber = 31;
for (let i = 0; i < classMateNumber; i++) {
    console.log("Elève" + 1);
}

const values = [1, 2, 3, 4, 5, 6, 7];

for (let i = 0; i < values.length; i++) {
    console.log("Elève" + values[i]);
}
// simplifiaction de i++
for (const value of values) {
    console.log("Elève" + value);
}
```

```JS
const student = ['Adrien', 'Juliette', 'Manon', 'Pierre'];

for (const value of student) {
    console.log(value);
}

// forme de liste énuméré
for (const key in student) {
    console.log(`${parseInt(key) + 1}. ${student[key]}`);
}
```

```JS
// boucle while a l'envers

const classMateNumber = 31;
let i = 0;
do {
    console.log("Elève " + i);
    i++;
} while (classMateNumber > i);
```

```JS
// Mot clé / Keyword
// while (condition d'ârret) {// code}

const classMateNumber = 31;
let i = 0;
while (classMateNumber > i) {
    console.log("Elève " + i);
    i++;
}
```

```JS
const arrClassMatesNumber = [];
const otherArr = arrClassMatesNumber;

arrClassMatesNumber[31] = "bam";
console.log("arrClassMateNumber", arrClassMatesNumber.length, arrClassMatesNumber)
```

## Fonctions

### Pourquoi les fonctions

**code unique**

- modification centralisé
- debug facilité
- gain de temps
- moins d'erreurs
- une seule responsabilité

**fonction récursive**

- exercice chrono

**fonction setTimeout**

```js
function displayBoom() {
    console.log("boom");
}

console.log(displayBoom, 3000);
```

**fonction anonyme**

```JS
// algo anonyme qu'on appelle directement
(function () {
    //some code
})();

// algo anonyme appellée au bout de 200ms
setTimeout(function () {
    console.log("boom");
}, 200)

// depuis ES6 (algo callback)
setTimeout(() => {
    console.log("boom");
}, 200)

```

**fonction callback**

```js
const prenom = "Adrien";

function addSuffixe(oldName, suffix, cb) {
    if (cb) cb();
    return oldName + suffix;
}

const transformName = addSuffixe(prenom, "bam", () => console.log(prenom));
const other = addSuffixe(prenom, "boom");
console.log(transformName, other);
```

## DOM ET JS

**document.querySelector**

```js
const htmlEL = document.querySelector("#idVoulu");

// l'élément avec id #uniqueId
const htmlElUniqueId = document.querySelector("#ID");
```

**Evenement**

- click
- scroll
- mousemove
- et bien d'autres

**click**

```js
const btnDiv = document.getElementById("counterBtn");
btnDiv.addEventListener("click", anyFunction);
```

_exemple:_

```js
// sur une page HTML avec une div et des id
document.getElementById("#description");
const desc = document.getElementById("#description");
// console.log
desc.addEventListener("click", () => {
    console.log("click on div");
});

// changement style
desc.addEventListener("click", () => {
    des.style.fontSize = 48;
});
```

**create / remove element**

```js
containerEl.innerHTML = "<div>une div</div>";
const newEl = document.createElement("div");
containerEl.append(newEl);
newEl.remove();
```

## ARRAY

**Instanciation d'un tableau**

```js
const anArray = [1, "metz", {school: "MNS", group: "DW2"}];
const anArrayOld = new Array(1, "Metz", {school: "MNS", group: "DW2"});
console.log(anArrayn)
console.log(anArrayOld); // [1, "Metz", {school : "MNS", group : "DW2"}]
```

## Array : méthodes

### Fonctions de manipulation de tableaux en JavaScript

#### Ajouter / Supprimer des éléments :

- `push()`: Ajoute un ou plusieurs éléments à la fin du tableau et retourne la nouvelle taille du tableau.

```js
const array = [1, 2, 3];
array.push(4);
console.log(array); // Output: [1, 2, 3, 4]
array.push(5, 6);
console.log(array); // Output: [1, 2, 3, 4, 5, 6]
```

- `pop()`: Supprime le dernier élément du tableau et le retourne.

```js
const array = [1, 2, 3, 4, 5];
const poppedElement = array.pop();
console.log(poppedElement); // Output: 5
console.log(array); // Output: [1, 2, 3, 4]
```

- `shift()`: Supprime le premier élément du tableau et le retourne.

```js
let fruits = ['pomme', 'banane', 'orange'];
let firstFruit = fruits.shift();
// fruits est maintenant ['banane', 'orange']
// firstFruit est maintenant 'pomme'
```

- `unshift()`: Ajoute un ou plusieurs éléments au début du tableau et retourne la nouvelle taille du tableau.

```js
let fruits = ['banane', 'orange'];
let newLength = fruits.unshift('pomme');
// fruits est maintenant ['pomme', 'banane', 'orange']
// newLength est maintenant 3
```

#### Modifier des éléments :

- `splice()`: Ajoute ou supprime des éléments à partir d'un indice spécifié.

```js
let fruits = ['pomme', 'banane', 'orange'];
fruits.splice(1, 1, 'fraise', 'cerise');
// fruits est maintenant ['pomme', 'fraise', 'cerise', 'orange']
```

- `slice()`: Retourne une portion du tableau sélectionnée en fonction de l'indice de début et de fin.

```js
let fruits = ['pomme', 'fraise', 'cerise', 'orange'];
let selection = fruits.slice(1, 3);
// selection est ['fraise', 'cerise']

```

#### Rechercher / Filtrer des éléments :

- `indexOf()`: Retourne le premier indice de l'élément spécifié dans le tableau.

```js
let fruits = ['pomme', 'fraise', 'cerise', 'orange'];
let index = fruits.indexOf('fraise');
// index est 1
```

- `lastIndexOf()`: Retourne le dernier indice de l'élément spécifié dans le tableau.

```js
let fruits = ['pomme', 'fraise', 'cerise', 'orange', 'fraise'];
let lastIndex = fruits.lastIndexOf('fraise');
// lastIndex est 4
```

- `find()`: Retourne la première valeur qui satisfait une condition spécifiée.

```js
let numbers = [10, 20, 30, 40];
let result = numbers.find(num => num > 25);
// result est 30
```

- `filter()`: Crée un nouveau tableau avec tous les éléments qui passent un test spécifié.

```js
let numbers = [10, 20, 30, 40];
let filteredNumbers = numbers.filter(num => num > 25);
// filteredNumbers est [30, 40]

```

#### Parcourir des éléments :

- `forEach()`: Exécute une fonction donnée une fois pour chaque élément du tableau.

```js
let fruits = ['pomme', 'fraise', 'cerise', 'orange'];
fruits.forEach(fruit => console.log(fruit));
// affiche chaque fruit dans la console
```

- `map()`: Crée un nouveau tableau avec les résultats de l'appel d'une fonction pour chaque élément du tableau.

```js
let numbers = [1, 2, 3, 4];
let doubledNumbers = numbers.map(num => num * 2);
// doubledNumbers est [2, 4, 6, 8]
```

#### Vérifier des éléments :

- `includes()`: Détermine si un tableau contient une valeur spécifique.

```js
let fruits = ['pomme', 'fraise', 'cerise', 'orange'];
let includesOrange = fruits.includes('orange');
// includesOrange est true
```

- `some()`: Vérifie si au moins un élément du tableau passe un test spécifié.

```js
let numbers = [10, 20, 30, 40];
let hasGreaterThan25 = numbers.some(num => num > 25);
// hasGreaterThan25 est true
```

- `every()`: Vérifie si tous les éléments du tableau passent un test spécifié.

```js
let numbers = [10, 20, 30, 40];
let allGreaterThan5 = numbers.every(num => num > 5);
// allGreaterThan5 est true
```

#### Autres opérations :

- `sort()`: Trie les éléments d'un tableau localement.

```js
let fruits = ['orange', 'pomme', 'fraise', 'cerise'];
fruits.sort();
// fruits est ['cerise', 'fraise', 'orange', 'pomme']
```

- `reverse()`: Inverse l'ordre des éléments du tableau.

```js
let fruits = ['orange', 'pomme', 'fraise', 'cerise'];
fruits.reverse();
// fruits est ['cerise', 'fraise', 'pomme', 'orange']
```

- `concat()`: Fusionne deux ou plusieurs tableaux.

```js
let fruits1 = ['pomme', 'fraise'];
let fruits2 = ['orange', 'cerise'];
let allFruits = fruits1.concat(fruits2);
// allFruits est ['pomme', 'fraise', 'orange', 'cerise']
```

- `join()`: Rassemble tous les éléments d'un tableau dans une chaîne de caractères.

```js
let fruits = ['pomme', 'fraise', 'orange', 'cerise'];
let fruitString = fruits.join(', ');
// fruitString est 'pomme, fraise, orange, cerise'
```

- `isArray()`: Vérifie si une variable est un tableau.

```js
let fruits = ['pomme', 'fraise', 'orange', 'cerise'];
let isArrayOfFruits = Array.isArray(fruits);
// isArrayOfFruits est true
```

## les objets

```js
const opel = {name: "Opel", from: "GER"}
const ford = {name: "Ford", from: "USA"}
const marc = {firstname: "Marc", lastname: "Pablito"}

const corsa = {
    brand: opel,
    color: "red",
    driver: marc
}

const f150 = {...corsa};

corsa.color = "green";

f150.brand = ford;

const mercedes = {...ford, name: "Mercedes"};

```

