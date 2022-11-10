# Teknisk studie om Load Balancers för REST API
Under projekts planering började vi räkna på hur många request REST APIet på ett ungefär kommer att ta emot (trafik) från alla våra program. Där exempelvis ett program gör förfrågningar om information om en viss scooter som är aktiv där scooterns information uppdateras var 10 sekund medans ett annat program gör en förfrågning om alla scootrar och städer.

Med detta kom vi fram till att mer än 10 000 request i minuten kommer att göras (Om man tänker att fler kommer att använda de olika programmen). Med detta behövde vi då kolla mer ingående på hur vi ska optimera prestandan och även se hur många request ett REST API faktist klarar av om man bygger det med nodejs och express utan med hjälp av en Load Balancer.

Vi började att göra en benchmark test för REST APIet med ApacheBench där vi testar hur långt tid det tar att göra 100 000 request till en sida på localhost som visar dokumentationen för REST APIet.


<img src="/v-teamAssets/benchmark1.png" alt="Benchmark 1" width="400"/>

 
Här kan vi läsa av att det tog 28.074 sekunder för att alla request ska gå igenom när man testade att göra 100 000 förfrågningar där 1000 förfrågningar görs åt gången.

## Load balancer
Vi kom fram till att använda en Load Balancer som fungerar som en trafikpolis som sitter framför applikationen och dirigerar klient förfrågningar till alla servrar (jobbare) som tar hand om requesten och uppfyller dem. Med att använda sig utav detta så säkerställer man att ingen server (jobbare) är överarbetad som kan försämra prestandan. Även så maximerar man hastigheten för alla request där det är fler jobbare som kan jobba på olika saker (hanterar arbetsbelastningen) än att utan en load balancer så finns det bara en jobbare som kan jobba på just den saken. Ett Exmempel på en Load Balancer är NodeJS egna cluster modul som vi kommer att använda oss utav i vårat projekt. Det tog ungefär 18,7 sekunder för 100 000 förfrågningar där 1000 förfrågningar görs åt gången. Detta är då ungefär 10 sekunder snabbare än tidigare benchmark test med att ladda en sida med information men kommer troligtvis vara snabbare när det är olika sorters förfrågningar som görs.

Bild på Benchmark när Cluster modulen används i REST APIet.


<img src="/v-teamAssets/benchmark2.png" alt="Benchmark 2" width="400"/>

## NodeJS egna Cluster Modul
Nodejs har en egen inbyggd modul som heter Cluster Module för att kunna ta del av ett flerkärnigt system än vad som är förinställt för just NodeJS som bara använder sig utav en enda tråd ( Kärna ) på ett flerkärnigt system. För att dra nytta av de andra tillgängliga kärnorna kan man starta ett kluster av Node.js-processer och fördela belastningen mellan dem.

Att ha flera trådar för att hantera förfrågningar förbättrar genomströmningen (förfrågningar/sekund) på sin server eftersom flera klienter kan betjänas samtidigt.

NodeJS cluster modulen skapar underordnande processer såkallat arbetare som körs samtidigt och delar samma serverport. Varje skapad arbetare har egen händelseloop, minne och v8-instans som gör att fler förfrågningar kan behandlas samtidigt och om det finns en långvarig/blockerande operation på en arbetare kan de andra arbetare fortsätta hantera andra inkommande förfrågningar. Alltså att REST APIet inte kommer att bli blockerad / sluta att funka tills förfrågningen som blockeras är behandlad.

Masterprocessen lyssnar efter anslutningar på en port och fördelar dem över arbetarna på ett round-robin-sätt.
Masterprocessen skapar en lyssningskontakt och skickar den till intresserade arbetare som sedan kan ta emot inkommande anslutningar direkt.

Nedan visar jag en bild där det finns en primary (Masterprocessen) och ett antal arbetare som jobbar på samma port för att ta hand om alla förfråningar.


<img src="/v-teamAssets/worker.png" alt="workers" width="400"/>


### Använda NodeJS CLuster Module
Dokumentation - https://nodejs.org/api/cluster.html

Finns även flera sidor och videos som visar hur man implementerar det.

## Andra Load Balancers
Det finns även andra Load Balancers som man kan använda sig utav.
Exempelvis på detta är:
- Nginx
- Express Web Server Balancer
- HAProxy

Vi valde att använda oss utav NodeJS egna modul för att det kändes lättast att implementera med den kunskapen vi har men finns säkert bättre Load Balancers.
