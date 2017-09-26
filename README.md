Wij gaan een barkassasysteem bouwen. Het idee hierachter is dat gebruikers een rekening hebben en op verschillende manieren kunnen betalen met deze rekening. Dit zal in ieder geval gebeuren met QR-codes. Voor nu zullen we deze intypen in plaats van scannen. We houden de optie open om later eventueel gezichtsherkenning en NFC-readers te gebruiken om te betalen. 

De volgende gegevens worden in ieder geval opgeslagen in de database: 
- Gebruikers
- Verificatiemethoden (QR, NFC, gezicht) (incl. start- en einddatum)
- Producten (incl. start- en einddatum)
- Prijzen (incl. start- en einddatum)
- Transacties
- Saldo ophogingen
- Verzonden berichten

De volgende gegevens worden optioneel opgeslagen in de database: 
- Kortingen (incl. start- en einddatum)
- Kortingsbonnen (incl. start- en einddatum)
- Groepen (tijdelijk 1 gezamenlijke rekening) (incl. start- en einddatum)

Als vervanging voor een database gebruiken we het filesysteem. Ik zal hiervoor een reeks functies schrijven die we makkelijk kunnen gebruiken om te queryen op text en csv files. Ikzelf zal een ERD gaan bouwen voor de database. 

Een transactie met ons kassasysteem werkt als volgt: 
- Een gebruiker kiest een product dat hij wilt kopen
- De medewerker slaat de producten aan in de GUI
- De gebruiker scant zijn verificatiemethode (QR, NFC of gezicht)
- De transactie wordt toegevoegd in de database
- Het saldo van de gebruiker wordt aangepast
- Er wordt een bericht gestuurd via Telegram naar de gebruiker die verteld dat er een transactie gedaan is. Eventueel wordt er duidelijk gemaakt dat zijn saldo laag of op is. 
- Einde transactie

De volgende handelingen moeten vanuit de GUI kunnen: 
- Geld storten
- Transactie maken
- Nieuw gebruikersaccount aanmaken
- Nieuwe betaalmethode aan account koppelen
- Prijzen wijzigen
- Kortingen/acties toevoegen

Gebruikersgegevens worden versleuteld. Het gebruikers-ID en saldo worden niet versleuteld om de snelheid van de applicatie op peil te houden. 

Saldo van een gebruiker staat direct op het account. Dit omdat het inefficiënt werkt als je bij elke transactie het saldo van de gebruiker uit moet rekenen. Er komt wel een functie die controleert of het saldo overeen komt met alle transacties en saldo ophogingen. Zo niet, dan geeft deze functie de optie om dit aan te passen. 

We voegen ook een grafiek toe (nog niet duidelijk welke) die weergeeft wat de omzet was. 

Optioneel: 
- Gezichtsherkenning om te betalen
- NFC om te betalen
- Buienradar API die bericht stuurt als het lekker weer wordt ("Biertje?")
- Tijdelijke gezamelijke rekening. Als 1 persoon in een tijdelijke groep betaald, wordt er een gelijk bedrag afgeschreven van alle rekeningen in de groep. 
- Kortingen versturen via Telegram
- Kortingsbonnen
