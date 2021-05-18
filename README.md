# cadAR
En AR-applikation med tillhörande [hemsida(https://s3.amazonaws.com/hardkodarna.se/index.html "CAD-ARs hemsida")] för visualisering av konstruerade CAD-objekt. 

## Funktion och användande

### Bakgrund
Problem med att veta hur ett datordesignat objekt passar in i den verkliga miljön är vardagsmat för oss som arbetar med CAD och konstruktion. Vi i gruppen fick nog av dessa problem och bestämde oss för att göra något åt det genom att skapa en AR-applikation där det är möjligt att se sina caddade objekt i en verklig miljö. I denna GitHub kan du läsa mer om vårt projekt och få fördjupad information om varje enskild del. Dessutom kan du själv testa både vår hemsida och vår AR-applikation för mobiltelefoner byggd med Unity. 

### Vad ska vi göra? 
Vi ska skapa ett AR-projekt där man kan testa sina caddade filer innan man skriver ut dem. Det går snabbt, smidigt och enkelt att se sina objektm med hjälp av vår applikation. Det gör att materialåtgången minskar då man i relatid kan testa sina objekt innan man skriver ut dem och på så sätt undvika att skriva ut onödiga filer som ändå inte passar in. Dessutom är det tidseffektivt eftersom man släpper lägga onödig tid på att vänta på låmngsamma 3D-skrivare. 

### Hur fungerar systemet?
1. Ladda upp din fil av typen obj på vår hemsida. Observera att filen måste vara i obj-format. 
2. Scanna den autogenererade QR-koden som då skapas med din mobiltelefon genom vår mobilapplikation.
3. Njut av att se ditt konstruerade objekt i realtid på din telefon. 

## Beskrivning av delsystem

### Hemsida

[Här kan du gå in på vår hemsida](https://s3.amazonaws.com/hardkodarna.se/index.html "CAD-ARs hemsida")

Hemsidan är byggd med Vue importerat in i en vanlig html-fil. Denna fil kan du finna under sökvägen "Hemsida/index.html". HTML-kodens script del består av två huvudskaliga delar. En del som är en modifiering av AWS egna exempelkod för att kunna skicka filer från en hemsida till en API, [här kan du se exempelkoden](https://github.com/aws-samples/amazon-s3-presigned-urls-aws-sam "AWS egen GitHub"). Den största skillnaden mellan AWS egna exempelalternativ och vår lösning är att de endast tillåter JPG-filer medan vi endast vill tillåta obj-filer. Därför ser koderna också mycket olika ut. På bilden nedan syns hur hemsidans startsida ser ut. 

![alt text](https://github.com/davidmorck/Hardkodarna/blob/main/Bilder/hemsida.PNG "Bild på hemsidan")

Den andra huvudsakliga delen av vår script-kod består av en kod som genererar en QR-kod i samband med att användaren laddar upp sin fil. För att skapa QR-koden används ett bibliotek för VUE vid namn QRious, [läs mer om Qrious här](https://www.npmjs.com/package/vue-qrious "QRious dokumentation"). Till QR-koden kopplas den information som finns i filen, således finns data med alla de vektorer vektorer som tillsammans bygger upp objektet lagrade på QR-koden. Utöver QR-koden skrivs också objektID:t ut på skärmen, något som syns på bilden nedan. 

![alt text](https://github.com/davidmorck/Hardkodarna/blob/main/Bilder/HemsidaQR.PNG "Bild på QR-kod från hemsidan")

Utöver det består hemsidans kod av lite CSS och några textrader med information som riktar sig till användaren. Dessutom finns ett par knappar där användaren kan ladda upp filer från den egna datorn. Hemsidans design är simpel och användarvänlig. Den är enkel i sin layout då fokus främst legat på funktion och AR-applikationens utseende. Hemsidans främsta syfte är att på ett enkelt sätt kunna erbjuda en smidig lösning för att ladda upp filer. Samtidigt som den ska kunna ge information till användaren kring funktion hos både hemsida och AR-applikation. 

Hemsidan hostas med hjälp AWS S3 och static website hosting. En smidig lösning för att på ett enkelt sätt hosta hemsidor gratis genom Amazon Web Services. 
### Backend
Backenden består av flera tjänster som finns hos AWS, en lambdafunktion, tre API:er och en S3-bucket. Lambdafunktionen aktiveras av den första API:n, som ska kallas på av hemsidan, som returnerar ett slumpat namn till objektet du vill ladda upp och URL:en till en ny API som man ska ladda upp objektet till. Den tredje API:n används av appen för att hämta objektet som laddats upp. 

![alt text](https://github.com/davidmorck/Hardkodarna/blob/main/Bilder/arvis.PNG "En förenklad modell av systemet")

### AR-applikation
Appen som användaren ska använda är snygg och praktisk och trots att mycket händer bakom kulisserna dras aldrig användaren ut ur upplevelsen.
#### Användargränssnitt
AR-appen har ett elegant och användarvänligt gränssnitt. Alla knappar är placerade på nedre halvan av skärmen vilket gör dem väldigt lättillgängliga för användaren. De eleganta knapparna och ikonerna är en fröjd för användarens ögon. Var man än är i appen så ser man vad kameran ser, detta är för att användaren tydligt ska förstå att detta är en AR-applikation.
| Det första användaren ska göra är att ange namnet på objektet (detta ska bytas ut till QR-scanning) | Efter användaren tryckt på hämta objekt så kommer hen till denna skärm | Efter en stund kommer nästa skärm med instruktioner upp | När användaren placerat ut objektet kan hen ta en skärmdump med hjälp av den inbyggda kameraknappen |
| ------------- | ------------- | ------------- | ------------- |
|![](https://github.com/davidmorck/Hardkodarna/blob/main/Bilder/AR-1.png)   |  ![](https://github.com/davidmorck/Hardkodarna/blob/main/Bilder/AR-2.png)|![](https://github.com/davidmorck/Hardkodarna/blob/main/Bilder/AR-3.png)   |  ![](https://github.com/davidmorck/Hardkodarna/blob/main/Bilder/AR-4.png)|

#### AR-programmering

## Framtidsvision
I framtiden skulle det vara spännande att fortsätta utveckla både applikation och hemsida för att få ett ännu bättre och mer felfritt system. Det skulle vara spännande att släppa applikationen tillgänglig för allmänheten på Android så att fler kan testa vårt system. Framtiden för AR-lösningar ser onekligen ljus ut och det används redan idag på olika sätt inom olika branscher. 

## Gruppinfo
Gruppen Hårdkodarna består av Amjad Alakrami, David Mörck och Joakim Eriksson
##### Har du frågor angående vårt projekt? Tveka då inte att höra av dig på mail. 
