# Readme

Se référerer à notre article pour plus d'exmplications [(lien)](https://inside.starfox-analytics.com/articles/gtm-bannieres-cookie-trigger-group-:-au-secours), et plus précisément à la dernière partie

## Points d'attention

* Dans les fichiers html de test nous avons inclus notre GTM avec un tag GA4 vers une propriété de test. Si vous voulez utiliser votre propre conteneur il n'y a qu'à changer l'indentifiant GTM

## Code de principe

```javascript
var variablesDePage = {'page_category': 'xxx', etc...} 
dataLayer.push(variablesDePage);

// préparer les différents dataLayer push à envoyer
function envoiEventsSupplementaires() {
  dataLayer.push({event: 'view_item_list', attributes...}) 
  // etc...
}

// gérer le consentement utilisateur
if (utilisateurADejaDonneSonConsentement) { // à adapter selon la CMP
	dataLayer.push({event: 'page_view'});
  sendEvents()
} else { // pas de choix utilisateur : il faut attendre le choix de l'utilisateur
  when (consentGiven) {
		dataLayer.push({event: 'page_view'});
    sendEvents()
}
```