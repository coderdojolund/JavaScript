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

5. Dags att skriva en funktion för att skriva ut ett meddelande. Här kommer du kunna få två alternativ: med hjälp av en if-else-sats samt med hjälp av så kallad boolean. En boolean kan vara sann eller falsk. T.ex. "Lakrits är gott": en del av oss tycker det är gott en del tycker det är mindre gott. Påståendet kan alltså vara sant eller falskt. Gör följande:

 a.	Skapa en funktion som heter `message` och tar in tre parametrar: `human`, `computer` och `humanIsWinner`.

 b.	Nu ska du se till så att om `humanIsWinner` är sant ska funktionen returnera följande: 

  -	'Du valde ' + human + ', datorn valde ' + computer + '; du vinner';

 c.	Om `humanIsWinner` är falskt ska funktionen returnera

  -	'Du valde ' + human + ', datorn valde ' + computer + '; du förlorar';

```javascript 
function message (human, computer, humanIsWinner) {
    if (humanIsWinner) {
        return 'Du valde ' + human + ', datorn valde ' + computer + '; du vinner';
    } else {
        return 'Du valde ' + human + ', datorn valde ' + computer + '; du förlorar';
    }
}
```

6.	Nu är det dags att jämföra ditt och datorns val. Detta gör du med hjälp av en funktion som du kallar compare(). compare ska ta två parametrar, human och computer. Detta gör du genom att skriva compare (human, computer) där human representerar ditt val och computer representerar datorns val. Ta följande steg:

 a.	Om human är lika med (===) computer, returnera 'Det är lika, ingen av er vinner';

 b.	Annars om (else if) human är lika med sten, gå in i en nästlad if-sats där:

  -	Om computer är lika med sax returnerar du: message (human, computer, true);  &ndash; Detta då true står för att du vinner.

  -	Annars (else) returnera message (human, computer, false); &ndash; Detta då false står för att du förlorar.

 c.	Avsluta nu den nästlade if-satsen.

 d.	Annars om human lika med sax, gå in i en nästlad if-sats där:

  -	Om computer är lika med sten, returnera message-funktionen + false.

  -	Annars returnerar du message-funktionen + true.

 e.	Avsluta nu den nästlade if-satsen.

 f.	Till sist gör du en sista koll med hjälp av en else if-sats om human är lika med påse samt en nästlad if else;

  -	Om computer är lika med sten, se till att funktionen message returnerar ett värde där användaren vinner.

  -	Annars returnerar du funktionen message och säger till att användaren förlorar.

```javascript
function compare (human, computer) {
    if (human === computer) {
        return 'Det är lika, ingen av er vinner';
    } else if (human === 'sten') {
        if (computer === 'sax') {
            return message (human, computer, true);
        } else {
            return message (human, computer, false);
        }
    } else if (human === 'sax') {
        if (computer === 'sten') {
            return message (human, computer, false);
        } else {
            return message (human, computer, true);
        }
    } else if (human === 'påse') {
        if (computer === 'sten') {
            return message (human, computer, true);
        } else {
            return message (human, computer, false);
        }
    }
}
```

7.	Dags att köra vårt spel och se resultatet. Skapa en funktion som heter play och i den ”kallar” du på alert(compare(userChoice(), computerChoice()));

8. Kör nu koden med "Run" i jsfiddle och testa spelet. Händer följande?

BILD

BILD

BILD

## Fullständig kod utan kommentarer

```javascript
function userChoice	() {
	return prompt('Vill du välja, sten, sax eller påse?');
}

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

function compare (human, computer) {
    if (human === computer) {
        return 'Det är lika, ingen av er vinner';
    } else if (human === 'sten') {
        if (computer === 'sax') {
            return message (human, computer, true);
        } else {
            return message (human, computer, false);
        }
    } else if (human === 'sax') {
        if (computer === 'sten') {
            return message (human, computer, false);
        } else {
            return message (human, computer, true);
        }
    } else if (human === 'påse') {
        if (computer === 'sten') {
            return message (human, computer, true);
        } else {
            return message (human, computer, false);
        }
    }
}

function message (human, computer, humanIsWinner) {
    if (humanIsWinner) {
        return 'Du valde ' + human + ', datorn valde ' + computer + '; du vinner';
    } else {
        return 'Du valde ' + human + ', datorn valde ' + computer + '; du förlorar';
    }
}

alert(compare(userChoice(), computerChoice()));
```
