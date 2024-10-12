# Checkpoint-Network-Requests-in-JavaScript

Voici comment vous pouvez créer une application météo en suivant les instructions fournies.

1. Mettre en place votre projet
Créez un nouveau dossier pour votre projet d'application météo.

Exemple de structure de dossier :

lua
/mon-app-meteo  
|-- index.html  
|-- styles.css  
|-- script.js  
2. Écrire la structure HTML
Contenu de index.html :

html
<!DOCTYPE html>  
<html lang="fr">  
<head>  
    <meta charset="UTF-8">  
    <meta name="viewport" content="width=device-width, initial-scale=1.0">  
    <title>Application Météo</title>  
    <link rel="stylesheet" href="styles.css">  
</head>  
<body>  
    <div class="container">  
        <h1>Application Météo</h1>  
        <input type="text" id="cityInput" placeholder="Entrez une ville">  
        <button id="searchButton">Rechercher</button>  
        <div id="weatherResult"></div>  
    </div>  
    <script src="script.js"></script>  
</body>  
</html>  
3. Style Your App with CSS
Contenu de styles.css :

css
body {  
    font-family: Arial, sans-serif;  
    background-color: #f0f0f0;  
    margin: 0;  
    padding: 20px;  
}  

.container {  
    max-width: 500px;  
    margin: 0 auto;  
    background: white;  
    padding: 20px;  
    border-radius: 8px;  
    box-shadow: 0 0 10px rgba(0, 0, 0, 0.1);  
}  

h1 {  
    text-align: center;  
}  

#weatherResult {  
    margin-top: 20px;  
    text-align: center;  
}  

@media (max-width: 600px) {  
    .container {  
        width: 90%;  
    }  
}  
4. Écrire du JavaScript pour récupérer des données météorologiques
Contenu de script.js :

javascript
const apiKey = 'VOTRE_API_KEY'; // Remplacez par votre clé API  
const searchButton = document.getElementById('searchButton');  
const cityInput = document.getElementById('cityInput');  
const weatherResult = document.getElementById('weatherResult');  

searchButton.addEventListener('click', () => {  
    const city = cityInput.value;  
    fetchWeatherData(city);  
});  

function fetchWeatherData(city) {  
    const url = `https://api.openweathermap.org/data/2.5/weather?q=${city}&appid=${apiKey}&units=metric`;  

    fetch(url)  
        .then(response => {  
            if (!response.ok) {  
                throw new Error('Erreur: ' + response.statusText);  
            }  
            return response.json();  
        })  
        .then(data => {  
            displayWeather(data);  
        })  
        .catch(error => {  
            weatherResult.innerHTML = `<p>${error.message}</p>`;  
        });  
}  

function displayWeather(data) {  
    const temperature = data.main.temp;  
    const description = data.weather[0].description;  
    const location = data.name;  

    weatherResult.innerHTML = `  
        <h2>Météo à ${location}</h2>  
        <p>${temperature}°C</p>  
        <p>${description}</p>  
    `;  
}  
5. Tester votre application
Ouvrez le fichier index.html dans votre navigateur web.
Entrez le nom d'une ville dans le champ de texte et cliquez sur "Rechercher".
Vérifiez que les informations météo sont récupérées et affichées correctement.
Surveillez la console du navigateur pour confirmer qu'il n'y a pas d'erreurs.
Note
N'oubliez pas d'obtenir et de remplacer VOTRE_API_KEY par une clé d'API valide depuis OpenWeatherMap.
Vous pouvez personnaliser le style ou le contenu selon vos préférences.
Avec ces étapes, vous devriez être en mesure de créer une application météo fonctionnelle.
