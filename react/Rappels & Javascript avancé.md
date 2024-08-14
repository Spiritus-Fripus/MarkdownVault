# Rappels & Javascript avancé

1. **ES6 et au-delà**
    - **let et const** :
        - **Définition et différences avec `var`** :
            - `let` et `const` introduisent une portée de bloc, tandis que `var` a une portée fonctionnelle.
            - `const` est utilisé pour déclarer des constantes, tandis que `let` est utilisé pour les variables dont la valeur peut changer.
        - **Exemples d'utilisation** :
```javascript

// var example
function varExample() {
  var x = 1;
  if (true) {
    var x = 2;  // Same variable!
    console.log(x);  // 2
  }
  console.log(x);  // 2
}

// let example
function letExample() {
  let x = 1;
  if (true) {
    let x = 2;  // Different variable
    console.log(x);  // 2
  }
  console.log(x);  // 1
}

// const example
const y = 1;
// y = 2;  // TypeError: Assignment to constant variable.

```

- **Bonnes pratiques** :
    - Utilisation de `const` par défaut, et `let` lorsque la variable doit être réassignée.
    - Éviter l'utilisation de `var` pour prévenir les bugs liés à la portée.
- **Fonctions fléchées**:
    - **Syntaxe des fonctions fléchées** :
        - Syntaxe concise pour écrire des fonctions anonymes.
```javascript

// Function expression
const add = function(a, b) {
  return a + b;
};

// Arrow function
const add = (a, b) => a + b;


```

- **Avantages** :
    - `this` lexical : les fonctions fléchées n'ont pas leur propre `this` ; elles capturent le `this` du contexte d'exécution dans lequel elles ont été définies.

```javascript

// Regular function
function Timer() {
  this.seconds = 0;
  setInterval(function() {
    this.seconds++;  // `this` refers to the global object, not the Timer instance
  }, 1000);
}

// Arrow function
function Timer() {
  this.seconds = 0;
  setInterval(() => {
    this.seconds++;  // `this` refers to the Timer instance
  }, 1000);
}


```

- **Exemples pratiques** :
    - Comparaison avec les fonctions traditionnelles.
    - Utilisation des fonctions fléchées dans des callbacks et des méthodes d'objets.
- **Classes**:
    - **Introduction aux classes en ES6** :
        - Syntaxe pour définir des classes et des constructeurs.

```javascript

class Person {
  constructor(name, age) {
    this.name = name;
    this.age = age;
  }

  greet() {
    console.log(`Hello, my name is ${this.name} and I am ${this.age} years old.`);
  }
}

const john = new Person('John', 30);
john.greet();  // Hello, my name is John and I am 30 years old.


```

- **Constructeurs et méthodes** :
    - Définir des méthodes dans une classe.
    - Initialisation des propriétés avec le constructeur.

```javascript 

class Car {
  constructor(make, model) {
    this.make = make;
    this.model = model;
  }

  displayInfo() {
    console.log(`This car is a ${this.make} ${this.model}.`);
  }
}

const myCar = new Car('Toyota', 'Corolla');
myCar.displayInfo();  // This car is a Toyota Corolla.


```

- **Héritage et polymorphisme** :
    - Utilisation de `extends` pour créer des sous-classes.
    - Appel de méthodes parent avec `super`.

```javascript

class Animal {
  constructor(name) {
    this.name = name;
  }

  speak() {
    console.log(`${this.name} makes a noise.`);
  }
}

class Dog extends Animal {
  speak() {
    console.log(`${this.name} barks.`);
  }
}

const dog = new Dog('Rex');
dog.speak();  // Rex barks.


```

- **Exemples pratiques** :
    - Création de classes et sous-classes avec des méthodes et des propriétés.
    - Utilisation de classes en React pour créer des composants.

2. **Asynchrone en JavaScript**
    - **Promises** :
        - **Concepts de base des Promises** :
            - Création de Promises avec `new Promise`.
            - États des Promises : pending, fulfilled, et rejected.

```javascript

const promise = new Promise((resolve, reject) => {
  const success = true;
  if (success) {
    resolve('The operation was successful.');
  } else {
    reject('The operation failed.');
  }
});

promise
  .then((message) => {
    console.log(message);  // The operation was successful.
  })
  .catch((error) => {
    console.error(error);
  });


```

- **Méthodes `.then()`, `.catch()`, et `.finally()`** :
    - Chaining des Promises pour gérer les opérations asynchrones séquentielles.
    - Gestion des erreurs avec `.catch()`.
    - Actions finales avec `.finally()`.

```javascript

javascriptCopier le code
const fetchData = () => {
  return new Promise((resolve, reject) => {
    setTimeout(() => {
      resolve('Data fetched');
    }, 1000);
  });
};

fetchData()
  .then((data) => {
    console.log(data);  // Data fetched
  })
  .catch((error) => {
    console.error(error);
  })
  .finally(() => {
    console.log('Operation completed');  // Operation completed
  });


```

- **Exemples pratiques** :
    - Création et utilisation de Promises pour les appels API.
    - Chaining de Promises pour des opérations asynchrones complexes.
- **Async/Await** :
    - **Introduction à `async` et `await`** :
        - Syntaxe pour écrire du code asynchrone de manière synchrone.
        - `async` pour déclarer des fonctions asynchrones.
        - `await` pour attendre la résolution d'une Promise.

```javascript

const fetchData = async () => {
  const response = await fetch('https://api.example.com/data');
  const data = await response.json();
  return data;
};

fetchData()
  .then((data) => {
    console.log(data);
  })
  .catch((error) => {
    console.error(error);
  });


```

- **Conversion de code basé sur les Promises en code `async/await`** :
    - Réécriture d'exemples de Promises avec `async/await`.

```javascript

// Using Promises
function fetchDataWithPromises() {
  return fetch('https://api.example.com/data')
    .then(response => response.json())
    .then(data => {
      console.log(data);
    })
    .catch(error => {
      console.error(error);
    });
}

// Using async/await
async function fetchDataWithAsyncAwait() {
  try {
    const response = await fetch('https://api.example.com/data');
    const data = await response.json();
    console.log(data);
  } catch (error) {
    console.error(error);
  }
}


```

- **Gestion des erreurs avec `try/catch`** :
    - Utilisation de `try/catch` pour gérer les erreurs dans les fonctions `async`.

```javascript

async function fetchData() {
  try {
    const response = await fetch('https://api.example.com/data');
    if (!response.ok) {
      throw new Error('Network response was not ok');
    }
    const data = await response.json();
    console.log(data);
  } catch (error) {
    console.error('Fetch error:', error);
  }
}

```

- **Exemples pratiques et cas d'utilisation en React** :
    - Appels API avec `async/await` dans les composants React.
    - Gestion des effets secondaires asynchrones avec les hooks.

```javascript

import { useState, useEffect } from 'react';

function DataFetchingComponent() {
  const [data, setData] = useState(null);
  const [loading, setLoading] = useState(true);
  const [error, setError] = useState(null);

  useEffect(() => {
    const fetchData = async () => {
      try {
        const response = await fetch('https://api.example.com/data');
        const result = await response.json();
        setData(result);
      } catch (error) {
        setError(error);
      } finally {
        setLoading(false);
      }
    };

    fetchData();
  }, []);

  if (loading) return <div>Loading...</div>;
  if (error) return <div>Error: {error.message}</div>;
  return <div>Data: {JSON.stringify(data)}</div>;
}


```

3. **Modules en JavaScript**
    - **Import/Export** :
        - **Syntaxe des imports et exports** :
            - Exportation de variables, fonctions, et classes avec `export` et `export default`.
            - Importation de modules avec `import`.

```javascript

// module.js
export const myFunction = () => {
  console.log('Hello from myFunction');
};

export const myVariable = 42;

// main.js
import { myFunction, myVariable } from './module.js';

myFunction();  // Hello from myFunction
console.log(myVariable);  // 42


```

- **Différence entre `default` et `named` exports** :
    - Utilisation de `export default` pour exporter une valeur par défaut.
    - Utilisation de `named exports` pour exporter plusieurs valeurs.

```javascript

// defaultExport.js
const defaultFunction = () => {
  console.log('Hello from default function');
};
export default defaultFunction;

// main.js
import defaultFunction from './defaultExport.js';
defaultFunction();  // Hello from default function


```

- **Bonnes pratiques pour structurer les modules** :
    - Organisation des fichiers de manière logique et modulaire.
    - Utilisation de `index.js` pour centraliser les exports.

```javascript

// utils/index.js
export { default as formatDate } from './formatDate';
export { default as parseDate } from './parseDate';

// main.js
import { formatDate, parseDate } from './utils';

```

- **Utilisation des modules ES6**:
    - **Organisation de projets en modules** :
        - Structurer un projet JavaScript avec des modules.
        - Meilleures pratiques pour nommer et organiser les modules.
    - **Importation de modules tiers** :
        - Utilisation de bibliothèques tierces avec `import`.
        - Gestion des dépendances avec npm et package.json.

```javascript

// Installation d'une bibliothèque tierce
// npm install lodash

// Utilisation de lodash dans un fichier
import _ from 'lodash';

const array = [1, 2, 3, 4];
const reversedArray = _.reverse(array.slice());
console.log(reversedArray);  // [4, 3, 2, 1]


```

- **Exemples pratiques d'organisation de projets React avec des modules** :
    - Modularisation des composants React.
    - Gestion des imports et des exports dans des projets React complexes.

```javascript

// components/Button.js
export const Button = ({ label, onClick }) => (
  <button onClick={onClick}>{label}</button>
);

// components/index.js
export { Button } from './Button';

// App.js
import { Button } from './components';

function App() {
  return (
    <div>
      <Button label="Click me" onClick={() => alert('Button clicked')} />
    </div>
  );
}

export default App;


```

4. **Manipulation du DOM**
    - **Sélection et modification d'éléments** :
        - **Sélectionner des éléments avec `document.querySelector` et `document.querySelectorAll`** :
            - Sélection d'éléments uniques et multiples.
            - Utilisation de sélecteurs CSS pour cibler les éléments.

```javascript

const singleElement = document.querySelector('.my-element');
const multipleElements = document.querySelectorAll('.my-elements');

console.log(singleElement);
multipleElements.forEach(element => console.log(element));


```

- **Modification des attributs, styles et contenu des éléments** :
    - Utilisation de propriétés comme `innerHTML`, `textContent`, et `classList`.
    - Modification des styles avec `style`.

```javascript

const element = document.querySelector('.my-element');

// Modifier le contenu
element.innerHTML = 'Hello, world!';
element.textContent = 'Hello, world!';

// Modifier les styles
element.style.color = 'blue';
element.style.fontSize = '20px';

// Ajouter et supprimer des classes
element.classList.add('active');
element.classList.remove('inactive');


```

- **Exemples pratiques de manipulation du DOM** :
    - Ajout, modification et suppression d'éléments dans le DOM.
    - Exemples interactifs pour illustrer la manipulation du DOM.

```javascript

// Ajouter un nouvel élément
const newElement = document.createElement('div');
newElement.textContent = 'New Element';
document.body.appendChild(newElement);

// Modifier un élément existant
const existingElement = document.querySelector('.existing-element');
existingElement.textContent = 'Updated Content';

// Supprimer un élément
const elementToRemove = document.querySelector('.remove-me');
elementToRemove.parentNode.removeChild(elementToRemove);


```

- **Événements** :
    - **Gestion des événements (addEventListener, removeEventListener)** :
        - Ajout et suppression d'écouteurs d'événements.
        - Utilisation des événements courants (clic, survol, etc.).

```javascript

const button = document.querySelector('button');

function handleClick() {
  console.log('Button clicked');
}

// Ajouter un écouteur d'événement
button.addEventListener('click', handleClick);

// Supprimer un écouteur d'événement
button.removeEventListener('click', handleClick);


```

- **Propagation et délégation des événements** :
    - Gestion de la propagation des événements avec `stopPropagation` et `preventDefault`.
    - Utilisation de la délégation d'événements pour gérer les événements sur des éléments dynamiques.

```javascript

// Propagation des événements
document.querySelector('.parent').addEventListener('click', (event) => {
  console.log('Parent clicked');
});

document.querySelector('.child').addEventListener('click', (event) => {
  event.stopPropagation();  // Arrête la propagation de l'événement
  console.log('Child clicked');
});

// Délégation des événements
document.querySelector('.list').addEventListener('click', (event) => {
  if (event.target && event.target.matches('li')) {
    console.log('List item clicked');
  }
});


```

- **Exemples pratiques d'interactions utilisateur** :
    - Implémentation de gestionnaires d'événements pour des interactions courantes.
    - Exemples d'interfaces utilisateur interactives.

```javascript

// Gestionnaire d'événements pour un formulaire
const form = document.querySelector('form');
form.addEventListener('submit', (event) => {
  event.preventDefault();  // Empêche l'envoi du formulaire
  console.log('Form submitted');
});

// Interaction avec un bouton
const button = document.querySelector('button');
button.addEventListener('click', () => {
  alert('Button clicked');
});


```

5. **Programmation fonctionnelle**
    - **Fonctions de première classe** :
        - **Définition des fonctions de première classe** :
            - Comprendre que les fonctions peuvent être traitées comme des valeurs.
            - Exemples de fonctions passées en arguments et retournées par d'autres fonctions.

```javascript

// Fonction de première classe
function greet(name) {
  return `Hello, ${name}`;
}

// Passer une fonction comme argument
function displayGreeting(greetingFunction, name) {
  console.log(greetingFunction(name));
}

displayGreeting(greet, 'Alice');  // Hello, Alice

// Retourner une fonction
function createMultiplier(multiplier) {
  return function(number) {
    return number * multiplier;
  };
}

const double = createMultiplier(2);
console.log(double(5));  // 10


```

- **Exemples pratiques d'utilisation de fonctions comme arguments et retours** :
    - Implémentation de callbacks et de fonctions d'ordre supérieur.
    - Utilisation de fonctions comme valeurs dans des structures de données.

```javascript

// Callback function example
function fetchData(callback) {
  setTimeout(() => {
    callback('Data fetched');
  }, 1000);
}

fetchData((data) => {
  console.log(data);  // Data fetched
});

// Higher-order function example
function applyOperation(a, b, operation) {
  return operation(a, b);
}

const add = (x, y) => x + y;
const result = applyOperation(3, 4, add);
console.log(result);  // 7


```

- **Fonctions d'ordre supérieur** :
    - **Définition et exemples de fonctions d'ordre supérieur** :
        - Fonctions qui prennent d'autres fonctions en argument ou qui retournent des fonctions.
        - Exemples courants comme `map`, `filter`, et `reduce`.

```javascript

// map example
const numbers = [1, 2, 3, 4];
const doubled = numbers.map(n => n * 2);
console.log(doubled);  // [2, 4, 6, 8]

// filter example
const evenNumbers = numbers.filter(n => n % 2 === 0);
console.log(evenNumbers);  // [2, 4]

// reduce example
const sum = numbers.reduce((acc, curr) => acc + curr, 0);
console.log(sum);  // 10


```

- **Utilisation de méthodes comme `map`, `filter`, et `reduce`** :
    - Manipulation de tableaux avec des fonctions d'ordre supérieur.
    - Exemples pratiques de transformation et de filtrage de données.

```javascript

// Transformation d'un tableau
const people = [
  { name: 'Alice', age: 25 },
  { name: 'Bob', age: 30 },
  { name: 'Charlie', age: 35 }
];

const names = people.map(person => person.name);
console.log(names);  // ['Alice', 'Bob', 'Charlie']

// Filtrage d'un tableau
const adults = people.filter(person => person.age >= 30);
console.log(adults);  // [{ name: 'Bob', age: 30 }, { name: 'Charlie', age: 35 }]

// Réduction d'un tableau
const totalAge = people.reduce((total, person) => total + person.age, 0);
console.log(totalAge);  // 90


```

- **Exemples pratiques et cas d'utilisation en React** :
    - Utilisation de fonctions d'ordre supérieur pour gérer l'état et les propriétés des composants.
    - Exemples de manipulation de listes et de collections de données dans des composants React.

```javascript

import { useState } from 'react';

function NamesList() {
  const [names, setNames] = useState(['Alice', 'Bob', 'Charlie']);
  const [filter, setFilter] = useState('');

  const filteredNames = names.filter(name => name.includes(filter));

  return (
    <div>
      <input
        type="text"
        value={filter}
        onChange={(e) => setFilter(e.target.value)}
        placeholder="Filter names"
      />
      <ul>
        {filteredNames.map(name => (
          <li key={name}>{name}</li>
        ))}
      </ul>
    </div>
  );
}


```

### Références et ressources supplémentaires:

- **Documentation officielle de JavaScript (MDN Web Docs)** :
    - [let et const](https://developer.mozilla.org/fr/docs/Web/JavaScript/Reference/Statements/let)
    - [Fonctions fléchées](https://developer.mozilla.org/fr/docs/Web/JavaScript/Reference/Functions/Fonctions_flechees)
    - [Classes](https://developer.mozilla.org/fr/docs/Web/JavaScript/Reference/Classes)
    - [Promises](https://developer.mozilla.org/fr/docs/Web/JavaScript/Reference/Global_Objects/Promise)
    - [Async/Await](https://developer.mozilla.org/fr/docs/Learn/JavaScript/Asynchronous/Async_await)
    - [Import/Export](https://developer.mozilla.org/fr/docs/Web/JavaScript/Reference/Statements/import)
    - [Déstructuration](https://developer.mozilla.org/fr/docs/Web/JavaScript/Reference/Operators/Destructuring_assignment)