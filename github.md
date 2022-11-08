# Hur man använder github i ett Team
## Sätta upp projektet i sin lokala mapp
Det första du behöver göra är att skapa en mapp i din lokala dator som du vill använda för ditt repository. Därefter behöver du initiera mappen med git och koppla den till repot och även sätta en main branch.
<pre>git init</pre>
<pre>git remote add origin git@github.com:<b>Repot här</b></pre>
<pre>git branch -M dev</pre>
Här sätter jag main branchen till dev då det är där alla implementationer kommer att skickas till - se mer i titeln **Branches** om varför jag har döpt den till dev.


Om det finns redan saker på main branchen eller i en annan branch som du ska använda dig utav, så behöver du hämta sakerna från den branchen så inte det blir commitments som är bakom. Detta gör du med pull:

<pre>git pull origin <b>dev</b></pre>

Där dev är den branchen som du vill hämta all data ifrån.

## Branches

![Branches](/v-teamAssets/branches.png "branches")


Att använda flera branches kommer att underlätta för ett team vilka featuters man implementerar. Även riskerar man inte att skada main branchen där programmet funkar. I våran grupp i V-Team grupp 1 har vi satt upp 2 branches som är de stora branches medans när vi implementerar feautres så skapar vi nya branches som därefter tas bort när de är klara, godkända av Reviewers och mergade till dev branchen.

### De olika branches vi använder oss utav:
- main (Där de stora releaserna sker från branch dev. Alltså att det går att köras och inga större buggar finns)
- dev (Där man implementerar feautersen och fixar buggar)
- Backlog branch - Där man skapar en nya branch för varje feautre som implementeras exempelvis: branch "setup" som vi ser på bilden, är en branch där vi sätter upp starten för programmet. Dessa branches kommer att tas bort efter att man har pushat sitt projekt och gjort en Pull Request som sedan en Reviewer kommer att kolla på implementationen och därefter merga den till dev branshen om allt ser bra ut och GitHuib Actions inte ger några varningar.

### Hur skapar man en branch vid varje feature?

Hur man skapar branch för varje feauture man ska implementera gör man:
<pre>git checkout -b <b>sidebar</b></pre>
Där **sidebar** är branchens namn som är en feautre som ska implementeras.
Alternativet **-b** är en bekvämlighetsflagga som säger åt Git att köra git branch innan git checkout 
< new-branch >.

Efter att du har skapat en ny branch där du ska implementera featuren som är du good to go att börja koda just den implementationen. När du är klar gör du:
<pre>git status</pre>
För att dubbelchecka att du är i den branchen och därefter lägger du till det du har gjort och pushar det:
<pre>git add <b>"de filerna du vill skicka upp / har ändrat till github"</b></pre>
<pre>git commit -m <b>"En kommentar vad du har gjort för något för just den filen"</b></pre>
Därefter ska du pusha den branshen med:
<pre>git push -u origin sidebar</pre>
Där **sidebar** är den branchen du vill pusha.
Därefter gör du git pull igen för att kolla om något har ändrats.
<pre>git pull origin dev</pre>
Därefter ska du skapa en pull request genom att gå in på den länken som står efter att du har pushat repot. Om du inte hittar länken så går du in på github och in i din branch.

När du är inne på rätt sida så tycker du på knappen:
**compare & pull request**


Där skriver du en titel vad det är för något du har gjort samt id på backlogen exempelvis:

*#3 Implemented sidebar*

Och sedan skriver en liten snabb text vad det är du har gjort så att reviewern kan kolla att det inte överstyr / skadar något annat och därefter trycker på knappen:
**Create pull request**
Om backlogen är helt klar så behöver du ta bort branchen på din dator efter att du har pushat och gjort en pull request. Hur du gör detta är att du går tillbaks till branch dev som är main branchen för devolopment ( Alla filer går dit ) och gör:
<pre>git checkout dev
git pull origin dev</pre>
För att ta bort branshen där du implementerade funktionen från backlog id så gör du exempelvis:
<pre>git branch -D sidebar</pre>
där **-D** är delete och **sidebar** är branchen.


Därefter så kan du börja göra nästa implementation med att skapa en ny branch.


***OPS glöm ej göra git pull när någon har mergat det du har implementerat / någon annan har implementerat så att du updaterad med alla filer som är skapade.***

## Settings
Att sätta regler på branches kan vara väldigt bra. I våran grupp har vi exempelvis regler i både main och dev branchen där man måste exempelvis skapa en pull request innan det går att merga till branchen. Även att man inte kan kringå ovanstående inställningar. I just main branchen har vi den låst då att det inte går att göra någon pull request och den sätts sedan på när dev branchen ska merga till main branchen när vi ska göra en del release på projektet. Vi har även satt default branchen till dev för att det ska vara lättare att göra git pull och även att pull requesten är förinställda på att merga till dev och inte main branchen.

Nedre bilden visar vilken branch som är satt på default och vilka branches som har protection rules på.
![Default branches](/v-teamAssets/branch1.png "Default branches")

Här visar jag protection rules för branch dev. I denna bracnh måste man göra en pull request för att man ska kunna merga sin branch till default branchen main. Även har jag satt att man inte kan bypassa pull request.

![Branch rules](/v-teamAssets/branchRule.png "Branch rules")

## Webhooks
Webhooks är väldigt användbart om man ska exempelvis använda sig utav Discord för sitt team. Detta hjälper med att exempelvis en Reviewer ska kolla på det någon annan har pushat. Även att man får notis om att nu kanske man ska göra en git pull för att hämta de nya filerna som har skapats. Github Webhooks skickar en notis till github serven till den chatten man har lagt in att boten ska skicka notiser till. Hur det kan se ut:
![Discord webhook](/v-teamAssets/webhook.png "Discord webhook")

Hur man sätter upp detta rekomenderar jag att kolla på denna tutorial från jagrosh: https://gist.github.com/jagrosh/5b1761213e33fc5b54ec7f6379034a22