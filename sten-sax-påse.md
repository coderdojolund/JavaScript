# Sten, Sax, Påse i Javascript &ndash; Vad gör all kod bakom dina Minecraft-moddar?

*Efter ett original av Marcus Mazur och Emy Spjuth, [tretton37 Lund](http://tretton37.se)*

Sten > Sax > Påse > Sten
* Sten vinner över sax
* Sax vinner över påse
* Påse vinner över sten

Vårt spel kommer att bestå av 3 steg:
1. Spelaren (du) gör ditt val.
2. Datorn gör sitt val.
3. En funktion avgör vem som vinner. 

En variabel är ett objekt som kan tilldelas ett värde. T.ex. `var x = 0`. `x` har nu värdet 0. Se exemplet nedan för att förstå hur man tilldelar ett värde till en variabel. *Du behöver inte mata in det här kodexemplet i datorn.*

```javascript
var x;
x = 0;
/* x har värdet 0 just nu */

x = 10;
/* Nu har x värdet 10 istället */
```

En JavaScript-funktion är ett kodblock för att utföra en viss uppgift. En funktion körs när något ”kallar” på funktionen.
*Du behöver inte mata in det här kodexemplet i datorn.*
```javascript
function subtract(num1, num 2) {
    return num1 - num2;
}

var result = this.subtract(5, 2);
/* result kommer att vara lika med 3 */

/* Man kan även se det så här */
this.subtract(5, 2);

/* Gör följande: */
function subtract(5, 2) {
    return 5 - 2;
}

/* result kommer att tilldelas värdet av vad funktionen returnerar; result är lika med 3 */
var result = 3;
```

En *if-else*-sats avgör antingen eller, t.ex. antingen är jag äldre än 10 eller yngre än 10. Se exempel nedan, vi kommer använda oss av if else senare och det är därför bra att bli bekant med den. 
*Du behöver inte mata in det här kodexemplet i datorn.*

```javascript
/* Math.random() kan vara allt från 0 till 1. T.ex. 0.56666 */
var random = Math.random();

if (random <= 0.34) {
    /* Anta att random får värdet 0.22; då hamnar vi här
       eftersom random är mindre än 0.34 */
  } else if (random <= 0.67) {
    /* Anta att random får värdet 0.55; då hamnar vi här
       eftersom random är mindre än 0.67 */
  } else {
    /* Anta att random får värdet 0.99; då hamnar vi här
       eftersom random inte uppfyller kraven för första if eller andra else if. */
}
```

# Skapa ett konto på jsfiddle

Skärmdump

# Vi kodar spelet

3.	Dags att börja programmera; du måste först ta reda på vad du själv väljer. Till detta skapar vi en funktion som heter `userChoice()`

 a.	Gör en funktion som heter `userChoice` och som returnerar `prompt(’Vill du välja, sten, sax eller påse?’)`

```javascript
function userChoice	() {
	return prompt('Vill du välja, sten, sax eller påse?');
}
```

 b.	Testa din funktion genom att ”kalla” på den. Detta gör du genom att skriva `alert(userChoice());`
 
```javascript
alert(userChoice());
```
 
 c.	Kör din kod genom att klicka på knappen *Run* i jsfiddle. Ser du följande? (BILD)
   - Ja: bra jobbat! 
   
   - Nej: ingen fara; fråga någon av mentorerna om hjälp. Det är helt ok att inte lyckas första gången.

4.	Dags att låta datorn göra sitt val; ja, det är helt möjligt. JavaScript har en inbyggd funktion som väljer en siffra mellan 0 och 1. Den kan exempelvis välja 0,5645454; detta kommer representera ett värde senare. Gör följande för att skapa en funktion som låter datorn avgöra vilket val den gjort.

 a.	Skapa en funktion som heter `computerChoice()`

 b.	I denna deklarerar du en variabel som heter `randomNumber`; denna variabeln tilldelar du värdet `Math.random();`

 c.	Nu är det dags att skriva *if-else*-satser och returnera valet för att avgöra vilket val datorn gör. Exempelvis såhär:
```javascript
	if (randomNumber <= 0.34) {
		return 'sten';
```
 - Gör följande:
  - Om randomNumber är större eller lika (<=) med 0.34 returnerar funktionen sten.
  -	Om randomNumber är större eller lika (<=) med 0.67 returnerar funktionen påse.
  - Om inget av dessa, returnerar den sax.
```javascript
function computerChoice	() {
	var randomNumber = Math.random();

	if (randomNumber <= 0.34) {
		return 'sten';
	} else if (randomNumber <= 0.67) {
		return 'påse';
	} else {
		return 'sax';
	}
}
```
