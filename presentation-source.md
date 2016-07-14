class: center middle

# Find.Me Architektur
### Ruben Gees, Alexej Esau

---

# Inhaltsverzeichnis

- Überblick

- CouchDB

  - API

- React.js Website

- Reacht Native App

---

# Überblick: Architekturdiagramm

![](img/architecture-diagram.png)

---

# CouchDB

![](img/architecture-diagram-highlight-couchdb.png)

---

.left-column[
## CouchDB
### Übersicht
]

.right-column[
- NoSQL Datenbank

  - Dokumentenbasiert

- Persistierung der Daten
]

---

.left-column[
## CouchDB
### Übersicht
### Schema
]

.right-column[
<center>
  <img src="img/couchdb-entity-relationship-diagram.png" width="100%"/>
</center>
]

---

# CouchDB API

![](img/architecture-diagram-highlight-couchdb-api.png)

---

.left-column[
## CouchDB API
### Übersicht
]

.right-column[
#### Ziel: Saubere Schnittstelle/Abstraktion zur Datenbank
- Enthält Sammlungen von DAOs

- Sowohl für React.js als auch für React Native
]

---

.left-column[
## CouchDB API
### Übersicht
### DAO
]

.right-column[
- Zugriffsschnittstelle für bestimmten Dokumententyp

- Bietet Methoden zum...

  - Erstellen von Objekten

  - Aktualisieren von Objekten

  - Löschen von Objekten

  - Suchen von Objekten anhand von Kriterien (Id, Name, ...)
]

---

.left-column[
## CouchDB API
### Übersicht
### DAO
### Beispiel: User
]

.right-column[
<center>
  <img src="img/userdao-diagram.png" />
</center>
]

---

.left-column[
## CouchDB API
### Übersicht
### DAO
### Beispiel: User
]

.right-column[

Callback Variante

```javascript
let login = "username";
let dm = new CouchDbApi.DaoManager(connSettings);
let userDao = dm.getDao(CouchDbApi.UserDAO);

userDao.findByLogin(login, {
    success: function(data) {
        // Do something with the data
    },
    error: function(err) {
        // Log/Show/Handle error
    }
});
```

Promise Variante

```javascript
let login = "username";
let dm = new CouchDbApi.DaoManager(connSettings);
let userDao = dm.getDao(CouchDbApi.UserDAO);

userDao.findByLogin(login)
    .then(function(data){
        // Do something with the data
    })
    .catch(function(err){
        // Log/Show/Handle error
    });
```
]

---

# React.js Website

![](img/architecture-diagram-highlight-reactjs.png)

---

.left-column[
## React.js Website
### Übersicht
]

.right-column[
- JSX-UI Framework

- Entwickelt durch Facebook

- Entwicklung mittels JavaScript Komponenten (Objekte/Klassen)

- Ausschließlich UI Framework

- Kein Business Logic Layer
]

---

.left-column[
## React.js Website
### Übersicht
### Weitere Technologien
]

.right-column[
- Npm

- Webpack

- Karma

- Jasmine

- eslint

- Babel
]

---

.left-column[
## React.js Website
### Übersicht
### Weitere Technologien
### Viewerzeugung
]

.right-column[
#### Projektstruktur
![](img/reactjs-project-structure.png)
]

---

.left-column[
## React.js Website
### Übersicht
### Weitere Technologien
### Viewerzeugung
]

.right-column[
#### Ausgangssituation
<img src="img/browser-empty.png" width="100%"/>
]

---

.left-column[
## React.js Website
### Übersicht
### Weitere Technologien
### Viewerzeugung
]

.right-column[
#### Formaler Ablauf
<img src="img/reactjs-view-creation.png" style="max-height:600px"/>
]

---

.left-column[
## React.js Website
### Übersicht
### Weitere Technologien
### Viewerzeugung
]

.right-column[
#### Endergebnis
<img src="img/browser-loginpage.png" width="100%"/>
]

---

# Reacht Native App

![](img/architecture-diagram-highlight-react-native.png)

---

.left-column[
## React Native App
### Übersicht
]

.right-column[
- Framework zum Schreiben von nativen Apps für Android und IOs mithilfe von
  Javascript

- Ausführen von JavaScript zur Laufzeit und Darstellung in nativen Komponenten
  wie zum Beispiel einer `TextView`

- Vorteil: Nutzung der vielen bestehenden Bibliotheken für Javascript und
  verhältnismäßig einfache Implementierung
]

---

.left-column[
## React Native App
### Übersicht
### Bibliotheken
]

.right-column[
- lodash: Helferfunktionen

- react-native-vector-icons: Verschiedene Icons für zum Beispiel die Toolbar

- react-native-image-picker: Zum Aufnehmen oder Auswählen von Fotos
]

---

.left-column[
## React Native App
### Übersicht
### Bibliotheken
### Projektaufbau: Übersicht
]

.right-column[
![](img/react-native-structure.png)

- Verschiedene Konfigurationsdateien für Deployment und Verwaltung

- `android` enthält vorgegebene Projektstruktur von React Native (Gradle wird     genutzt)

- `node_modules` enthält JavaScript Bibliotheken
]

---

.left-column[
## React Native App
### Übersicht
### Bibliotheken
### Projektaufbau: Komponenten
]

.right-column[
![](img/react-native-structure-components.png)

- Aufteilung in frontend und backend

  - frontend enthält View Komponenten die an mehreren Stellen benutzt werden

  - backend enthält Klassen zum Datenzugriff
]

---

.left-column[
## React Native App
### Übersicht
### Bibliotheken
### Projektaufbau: Screens
]

.right-column[
![](img/react-native-structure-screens.png)

- Alle verschiedenen Screens ohne besondere Hierachien
]
