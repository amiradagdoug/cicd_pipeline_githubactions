ESLint in GitHub Actions
Ziel: Richte ein GitHub-Repository mit ESLint ein, um deinen Code-Stil zu überprüfen, und integriere es in einen GitHub Action Workflow. Du wirst Code schreiben, der
Linter-Warnungen erzeugt, und diese dann basierend auf den ESLint-Rückmeldungen korrigieren.
Schritt-für-Schritt-Anleitung
ESLint in GitHub Actions
Schritt-für-Schritt-Anleitung
Schritt 1: Anlegen des GitHub-Repositories
Schritt 2: Einrichten des Node.js-Projekts
Schritt 3: Konfigurieren von ESLint
Schritt 4: Erstellen von JavaScript-Dateien
Schritt 5: Einrichten von GitHub Actions
Schritt 6: Hinzufügen einer .gitignore Datei
Schritt 7: Pushen des Codes und Überprüfen der GitHub Action
Schritt 8: Beheben von Linter-Warnungen
Schritt 9: Erfolgreicher Abschluss
Schritt 1: Anlegen des GitHub-Repositories
1. Repository erstellen:
Gehe zu GitHub und erstelle ein neues Repository.
Gib ihm einen aussagekräftigen Namen, z.B. eslint-ci-demo .
2. Repository klonen:
Klone das Repository auf deinen lokalen Computer.
Nutze dafür den Befehl:
git clone <URL-deines-Repositories>
Wechsle in das Verzeichnis des Repositories:
cd eslint-ci-demo
Schritt 2: Einrichten des Node.js-Projekts
1. Node.js-Projekt initialisieren:
Initialisiere ein neues Node.js-Projekt:
npm init -y
2. ESLint installieren:
Installiere ESLint in deinem Projekt:
npm install eslint --save-dev
Schritt 3: Konfigurieren von ESLint
1. ESLint initialisieren:
Führe den Befehl aus und folge den Anweisungen:
npx eslint --init
Dies erzeugt eine Datei mit dem Name .eslintrc.js . Sie enthält die Konfiguration von ESLint.
Ersetze den Inhalt der Datei mit folgendem:

module.exports = {
"env": {
"node": true, // Definiert Umgebungsvariablen für Node.js
"es2021": true // Legt fest, dass der Code ECMAScript 2021 entsprechen soll
},
"extends": "eslint:recommended", // Verwendet die empfohlenen ESLint-Regeln
"parserOptions": {
"ecmaVersion": 12 // Erlaubt die Verwendung von ECMAScript 2021 Features
},
"rules": {
"indent": ["error", 4], // Erzwingt eine Einrückung von 4 Leerzeichen
"linebreak-style": ["error", "unix"], // Erzwingt Unix-Zeilenumbrüche (LF)
"quotes": ["error", "double"], // Verwendet doppelte Anführungszeichen für Strings
"semi": ["error", "always"], // Verlangt Semikolons am Ende der Anweisungen
"space-before-blocks": ["error", "always"], // Erzwingt ein Leerzeichen vor Klammern
"keyword-spacing": ["error", { "before": true, "after": true }], // Stellt sicher, dass Schlüsselwörter wie if, else, for, usw. korrekt von Leerzeichen umgeben sind
"space-infix-ops": "error", // Verlangt Leerzeichen um Operatoren
"space-before-function-paren": ["error", "always"], // Erzwingt Leerzeichen vor den Klammern von Funktionsdefinitionen
"space-in-parens": ["error", "never"], // Keine Leerzeichen innerhalb von Klammern
"object-curly-spacing": ["error", "always"], // Erzwingt Leerzeichen innerhalb von geschweiften Klammern
"array-bracket-spacing": ["error", "never"] // Keine Leerzeichen innerhalb von eckigen Klammern
}
};

Schritt 4: Erstellen von JavaScript-Dateien
1. JavaScript-Dateien erstellen:
Erstelle zwei JavaScript-Dateien, file1.js und file2.js , in deinem Projektverzeichnis mit Code, der gegen einige deiner ESLint-Regeln verstößt.
file1.js :
function greet(name){
console.log("Hello, "+ name +"!");
}
greet("World")
file2.js :
const add=(a,b)=>{
return a+b;
}
console.log(add(2, 3))
Schritt 5: Einrichten von GitHub Actions
1. Workflow-Ordner erstellen:
Erstelle im GitHub-Repository einen Ordner .github/workflows .
2. Workflow-Datei erstellen:
Erstelle eine YAML-Datei für deinen Workflow, z.B. lint.yml , mit folgendem Inhalt:

name: Lint Code
on: [push, pull_request]
jobs:
lint:
runs-on: ubuntu-latest
steps:
- name: Checkout Repository
uses: actions/checkout@v2
- name: Set up Node.js
uses: actions/setup-node@v2
with:
node-version: '14'
- name: Install Dependencies
run: npm install
- name: Run Linter
run: npx eslint .
Schritt 6: Hinzufügen einer .gitignore Datei
1. Code committen und pushen:
Füge die Datei .gitignore mit folgendem Inhalt hinzu:
node_modules

Schritt 7: Pushen des Codes und Überprüfen der GitHub Action
1. Code committen und pushen:
Füge alle Dateien zum Git-Repository hinzu:
git add .
Committe die Änderungen:
git commit -m "Initial commit with linter setup"
Pushe die Änderungen zu deinem GitHub-Repository:
git push origin main
2. Überprüfe die GitHub Action:
Gehe zu GitHub und überprüfe unter „Actions“, ob der Workflow ausgelöst wurde und ob Fehler oder Warnungen vorliegen.
Schritt 8: Beheben von Linter-Warnungen
1. Linter-Warnungen korrigieren:
Überprüfe die Linter-Warnungen in der GitHub Action-Ausgabe.
Korrigiere die Warnungen in deinen lokalen Dateien gemäß den ESLint-Richtlinien. (siehe Ausgabe)
Du kannst ESLint auch lokal laufen lassen und somit vor dem Push prüfen, ob alle Fehler behoben sind mit dem Befehl:
npx eslint .
2. Änderungen committen und pushen:
Füge die geänderten Dateien hinzu und committe sie:
git add .
git commit -m "Fix linter warnings"
Pushe die Änderungen erneut:
git push origin main
Schritt 9: Erfolgreicher Abschluss

Überprüfe, ob die GitHub Action jetzt ohne Warnungen oder Fehler durchläuft. Wenn ja, hast du die Aufgabe erfolgreich abgeschlossen!