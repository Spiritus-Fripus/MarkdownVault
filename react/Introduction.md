# Introduction

Documentation officielle React : [https://react.dev/learn](https://react.dev/learn)

1. **Présentation de React**
    
    - Historique de React.
        
        - React a été créé par Jordan Walke, un ingénieur de Facebook, en 2011.L'objectif initial était de résoudre les défis liés à la gestion de l'interface utilisateur dans des applications web dynamiques et [interactives.La](http://interactives.La) première version de React a été utilisée sur la partie fil d'actualité de Facebook et sur Instagram.
        - **Contexte de la création**:
            - Avant React, les applications web utilisaient souvent des manipulations directes du DOM, ce qui pouvait devenir lent et difficile à gérer à mesure que les applications se complexifiaient.
            - React introduit le concept du Virtual DOM, une abstraction qui permet des mises à jour de l'interface utilisateur plus performantes et moins coûteuses.
        - **Présentation initiale au public**:
            - React a été rendu open source lors de la conférence JSConf US en mai 2013.
            - Cela a permis à la communauté de développeurs de contribuer et d'adopter React pour une variété de projets.
    - Pourquoi utiliser React ?
        
        **Avantages principaux**:
        
        - **Virtual DOM** :
            - Le Virtual DOM est une représentation légère du DOM réel qui permet à React de mettre à jour l'interface utilisateur de manière efficace.
            - Au lieu de mettre à jour le DOM directement, React crée un Virtual DOM, effectue les modifications nécessaires, puis compare le Virtual DOM avec le DOM réel pour n'appliquer que les changements nécessaires.
            - Cette approche réduit le nombre de manipulations coûteuses du DOM et améliore la performance des applications.
        - **Composants réutilisables** :
            - Les composants sont les blocs de construction de base de React.
            - Chaque composant encapsule sa propre logique et son interface, ce qui permet de le réutiliser dans différentes parties de l'application.
            - Cette réutilisabilité améliore la maintenance et l'évolutivité des applications.
        - **Unidirectional Data Flow** :
            - En React, les données circulent dans une seule direction, du parent vers les composants enfants, ce qui rend le flux de données plus prévisible et plus facile à déboguer.
            - Ce modèle simplifie la gestion de l'état et réduit les erreurs de synchronisation des données.
        - **Large écosystème et communauté** :
            - React bénéficie d'un large écosystème de bibliothèques et d'outils qui facilitent le développement.
            - Une grande communauté de développeurs contribue à l'amélioration continue de React et offre un soutien précieux à travers des forums, des conférences et des ressources en ligne.
        
        **Comparaison avec d'autres frameworks**:
        
        - **Angular** :
            - Angular utilise le two-way data binding (liaison bidirectionnelle des données) tandis que React utilise le one-way data binding (liaison unidirectionnelle).
            - Angular offre une solution complète avec de nombreuses fonctionnalités intégrées, tandis que React est plus léger et se concentre sur la bibliothèque de rendu d'interface utilisateur.
        - **Vue.js** :
            - Vue.js et React partagent des similitudes dans la gestion des composants et l'utilisation de templates.
            - Vue est souvent considéré comme plus facile à apprendre pour les débutants en raison de sa simplicité et de sa documentation détaillée.
        - **Svelte** :
            - Svelte adopte une approche compilée où le code est transformé en JavaScript vanilla au moment de la compilation, éliminant le besoin d'un runtime.
            - React, en revanche, utilise un runtime pour gérer le Virtual DOM et les mises à jour de l'interface utilisateur.
    - Cas d'utilisation courants.
        
        - **Facebook** :
            - React est utilisé pour différentes parties de l'interface utilisateur de Facebook, notamment le fil d'actualité et les interfaces de messagerie.
            - Facebook a développé React pour répondre à ses propres besoins d'évolutivité et de performance.
        - **Instagram** :
            - L'utilisation de React permet à Instagram de fournir une expérience utilisateur dynamique et interactive.
            - Des fonctionnalités comme le feed, les stories, et les messages utilisent des composants React pour rendre l'interface utilisateur fluide.
        - **Airbnb** :
            - Airbnb utilise React pour son interface utilisateur, permettant une gestion efficace des composants et une maintenance simplifiée.
            - Les interfaces utilisateur complexes et riches en fonctionnalités, comme les pages de recherche et de réservation, bénéficient de la modularité de React.
        
        **Scénarios typiques où React excelle**:
        
        - **Applications avec des interfaces utilisateur dynamiques et complexes** :
            - Les projets nécessitant des mises à jour fréquentes et dynamiques de l'interface utilisateur bénéficient de l'efficacité du Virtual DOM de React.
        - **Projets nécessitant une performance optimale grâce à la gestion efficace du DOM** :
            - Les applications qui nécessitent une haute performance, telles que les jeux en ligne ou les applications en temps réel, profitent de l'optimisation du Virtual DOM.
        - **Applications nécessitant une forte réutilisabilité des composants** :
            - Les systèmes de design et les bibliothèques de composants partagés dans des grandes entreprises trouvent en React un allié pour la réutilisation et la cohérence de leurs interfaces.
2. **Concepts de base**
    
    - Composants.
    
    Ici nous déclarons une fonction Logo permettant de créer un nouveau composant. Ce composant va renvoyer une image en HTML.
    
    On ajoute ensuite ce composant dans notre fonction App en l’appelant avec des balises <Logo />
    
    Pour l’url de cette image on envoie en “paramètre” via les props avec la clé “url” depuis la fonction App. Dans la fonction Logo on récupère alors les props et on accède à la clé “url” pour afficher l’image.
    
```javascript
   import logo from './logo.svg';
import './App.css';

function Logo(props) {
  return (
    <img src={props.url} className="App-logo" alt="logo" />
  )
}

function App() {
  return (
    <div className="App">
      <header className="App-header">
        <Logo url={logo}/>
        <p>
          Edit <code>src/App.js</code> and save to reload.
        </p>
        <a
          className="App-link"
          href="https://reactjs.org"
          target="_blank"
          rel="noopener noreferrer"
        >
          Learn React
        </a>
      </header>
    </div>
  );
}

export default App;

```
## State et setState
```javascript
import logo from './logo.svg';
import './App.css';
import React, { useState } from 'react';

function Logo(props) {
  const [count, setCount] = useState(0);
  return (
    <div>
      <img src={props.url} className="App-logo" alt="logo" />
      <span>{count}</span>
      <button onClick={() => setCount(count + 1)}>Test</button>
    </div>
  );
}

function App() {
  return (
    <div className="App">
      <header className="App-header">
        <Logo url={logo}/>
        <p>
          Edit <code>src/App.js</code> and save to reload.
        </p>
        <a
          className="App-link"
          href="https://reactjs.org"
          target="_blank"
          rel="noopener noreferrer"
        >
          Learn React
        </a>
      </header>
    </div>
  );
}

export default App;

```

## useEffect
```javascript
import React, { useState, useEffect } from 'react';

function Clock(){
    const [time, setTime] = useState(new Date().toLocaleTimeString());
    useEffect(() => {
        const interval = setInterval(() => {
        setTime(new Date().toLocaleTimeString());
        }, 1000);
        //useEffect crée un nouvel interval à chaque appel. 
        //On supprime donc l'ancien à chaque passage pour éviter la surcharge
        return () => clearInterval(interval);
    }, []);
    return (
        <div>
        <span>{time}</span>
        </div>
    );
}

export default Clock;
```
