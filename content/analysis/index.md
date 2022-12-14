---
Title: Analys
Description: Analys presentation
---

<div class="main" role="main">
    <div class = "technology">
    <div class = flex-container2

  <aside>
  <div class="Color"><a href = "/~adde22/dbwebb-kurser/design/me/portfolio/analysis/01_colors">Color analys</a>
  </div>
  <div class="Load"><a href = "/~adde22/dbwebb-kurser/design/me/portfolio/analysis/02_load">Load analys</a>
  </div>
  <div class="Design"><a href = "/~adde22/dbwebb-kurser/design/me/portfolio/analysis/03_design_principles">Design & principles analys</a>
</a>
</aside>
</div>
</div>
<br>
<br>
<br>
<br>
<br>
<h1> Analys av webbplatser </h1>

<p>Vi ska analysera webbplatsens utseende och <b>color</b> med verktyg och design principer.</p>
<ul class= "titel">
<li><a href ="https://www.migrationsverket.se/">Migrationsverket </a></li>
<li><a href ="https://www.skatteverket.se/privat.4.76a43be412206334b89800052864.html">Skatteverket </a></li>
<li><a href ="https://www.boplatssyd.se/">BoplatsSyd</a></li>
</ul>
<p>Dessa populära webbplatser har valts eftersom de har funnits länge och har erfarnhet vid att ta emot ett stort antal personer, de har även en hel del resurser vilket kan vara intressant att ta med i analysen eftersom de nog haft en del UX design teams som jobbat med designen.</p>

<p>Ytterligare 3 webbsidor som ska analysera efter <b>loading</b> kriterier med verktyg och design principer.</p>
<ul class= "titel">
<li><a href ="https://www.leoslekland.se/">Leos lekland </a></li>
<li><a href ="https://www.lego.com/sv-se">Lego Leksaker </a></li>
<li><a href ="https://www.liseberg.se/">Liseberg</a></li>

</ul>

<p>Ytterligare 3 webbsidor som ska analysera efter <b>design</b> kriterier med verktyg och design principer.</p>
<ul class= "titel">
<li><a href ="https://networkchuck.com/">Network Chuck </a></li>
<li><a href ="https://www.techseries.dev/backstage">Tech Lead YoutubeBackstage </a></li>
<li><a href ="https://xxlandco.com/">Tina Nguyen XxlandCo</a></li>

</ul>

<p>Dessa webbplatser har valts eftersom jag tycker att de har stort inflytande i mina beslut inom tech och uppskattar deras arbete?</p>

<h2> Metod Color </h2>

<p>Kan tar mig in i webbsidan och aktiverar inspect mode, och startar att kolla efter typsnitt och andra colours som kan var struliga att hitta med verktygen, jag skickar in webbplatsens url i verktygen <b>https://color.a11y.com/</b> och kollar kontraster och om den valideras. Medans jag skriver och tar in color-scheme tar jag och funderar om syftet bakom webbplatsen och vad den vill "signalera emotionellt" osv. Jag avslutar med analys om vad jag tror fungerar,inte fungerar med profilen de vill ha samt vad som jag tror signaleras </p>

<h2> Metod Load </h2>

Vi har använt med verktyget PageSpeed Insights och Firefox Devtools/Chrome Devtools att mäta laddningstider mobilt och dator. Testerna har vart baserat rent kring prestanda av olika slag enligt kraven. Jag tog och gjorde alla tester separat och stoppade in i excel, share/embed (PageSpeed,Firefox Devtools links). Sen tog jag och gick igenom med Chrome devTools igen och analyserade datan separat,storlek,hastighet osv och presentera datan till framtida analys och resultat.

<h2> Metod Design </h2>

Den metod som tillämpats är att utgå från <b>https://www.canva.com/learn/design-elements-principles/</b> och se vilka principer som verkar tar mest plats, dra slutsatser kring syfte och designen, om det "matchar" eller ej. Kan dessutom se webbsidan ur perspektivit ur <b>https://zizzogroup.com/blog/7-principles-of-design/</b>. identifiera och analysera enligt kmom06 uppbbyggnad i kraven <b>https://dbwebb.se/uppgift/utvardera-webbplatsers-designprinciper-v2 till XXland co har https://www.groovecommerce.com/ecommerce-blog/ecommerce-design-principles/ tillämpat</b>.

<h2> Resultat Color </h2>

<p>Sammanfattningsvis kan jag se hur psykologin bakom valen färgvalen har gjorts, de passar oftast in till syftet samt hur stor vikt av simpel vit bakgrund tillsammans med en vägledande accent färg genomsyrar alla dessa webbplatser. Simplistiskt med fungerande! Valen av typsnitt sticker inte heller ut, de verkar vara ganska standard men med liten variation mellan diverse rubriker finns. kan vara en medveten strategi,sa att den som tittar in inte ska blir allt för överstimulerad/överaskad. </p>

<h2> Resultat Load </h2>

<p>Sammanfattningsvis kan se att storleken av brukat av js/doms har stor betydelse samt bild kvalitet och animationer brukas, en kan se det starkast mellan liseberg och Lego eftersom deras storlek liknar varandra med prestandan skilljer sig starkt. Liseberg bearbetar dess content mycket mer effektivt. En brist som var tydlig var enligt DevTools "Script calling style recalculation" dvs inte bra strukturerad css, antagligen main css i olika filer, bilders storlek samt antalat dom som laddas.
<br>
<br>
Min laddstandard: 5-8 sec <br>
<br>
Anledning till lite extra tid kan vara att syftet av vissa sidor kan vara betydande och ha en hel del information, ger det lite utrymma att inte vara helt optimerat om sidans storlek ar mycket stor, ibland kan det gott ta en halv sekund extra beroende kring vem som använder sidan. En äldre person /icke van bryr sig inte mycket om hastighet och kan tillochmed vara stressigt med att sidorna hoppar snabbt till ny redirect etc.

Enligt tester och laddstandard vill jag ge nästan delad plats mellan Liseberg och Leo med Leo snar vinnare enligt avarage test points och storlek och användnings känsla, sidan navigas mycket snabbt trots bilder,animation,videos och mycket interaktion. Anledning till den delade platsen är att liseberg har mer content och storlek med enligt score skapat en optimerad hemsida(Bättre än Lego).Om bara storleken hade vart mindre kunde kanske den tagit lika snabbt att "loada" som Leo men nu tar den in "mer" visitors,historia och har mer räckvidd populäritets mässigt,därav kanske storleken kan rättfärdigas mer<br>
<br>

Den trend jag ser kring vad som kan bli bättre är smartare css, hantera allt samlat utan redirects,Hantera bild storleken. använd sig inte av third party javascript. De blir krockar och skapar segare laddningstid
<br>
<br>

</p>
<h2> Resultat Design </h2>

Kan se att dessa personsidor har en viss tanka till att knyta ann syfte och design. Hacker IT, Youtuber promo salesman, E-commerce. och de har lyckats! Gillar att se att det finnas en hel del utrymma att snygga till det med tack vara denna kurs och materialt vi har.Det finns ens lags template som de flesta använder i dagens läge vilket verkar vara att bruka, linjärt uppdelande, fokus av color kombinationer som fungerar och minimialism. att efterlikna varandra. Det finns utrymme att skapa roligare sidor med lite mer risktagande och fler tillämpande designprinciper. OBs ingen av sidarna fick 100 i acessability! vilket Tech lead hade sämst vilket jag gissade mig till innan med kontrasterna som användes.

<h2> Analys Color</h2>  
 
<p>Adrian:<br> <br> Lite tveskam till Boplats syds samt skatteverkets tomhet men mest inom Boplatsyd,Tycker det fanns lite för mycket tom/vit yta ibland och det gav mig lite av en uttrakad känsla hade kunnat vara lite mer av samma, lite mer av logotypens fina färger ut i webbplatsens delar. Tycker det finns en stark betoning till psykolgin bakom syftet av hemsidan samt kombination av accent färger, det lugna blue, alerta gul samt alarmerande red. Kan se en potientiell standard av liknande värden som boplatsyd och skatteverket vill signalera och/eftersom de har nästan samma färgschema!<br> <br>

Gloria: <br> <br>
"Webbplatserna förlitar sig på neutrala färger - svart och vitt och förmedlar en idé om elegans men samtidigt enkelhet. I synnerhet symboliserar svart en elegans genom webbplatserna.
Minimalist approach används som en kan till färgvalen till de 3 webbplatserna" Se hennes version till mer utvecklad analys (tidsbrist)

<h2> Analys Load </h2>

<p>Adrian:<br> <br>

Summasumarum verkar det finnas lita av ett pattern, äldre och stora hemsidor brukar har utdatering skriptning och sämre hantering av css, antagligen har de inte velat uppdatera tekniken. Normalize och samla css, smart bildhantering och storlekshantering med quality changes och inte använda sig av third party javascript med bra packeterare som bundle <br> <br>

Gloria: "Vissa sidor som Leo fungerar muyket snabbt men har mindre content, minimalt och hantera data lokalt med paket fungerar bra, precis det som vi lär oss i kursen!" <br> <br>

<br><br>

</p>

<h2>Analys Design </h2>

<p>Adrian:<br><br>

<p>De flesta verkar kunna skapa en snygg standard design men saknar lite kreativitet utanfor den standarden, det skapar lite av en trist känsla.</p>

<p>Gloria: "Snygg design, vill kunna skapande liknande, tycker de verkar vara lite lata gällande performance och acessability och kreativiteten, tycker Network chuck gjorde bäst jobb allt som allt!" <br> <br><p>

<h2>Referenser </h2>

<p>

https://www.canva.com/learn/design-elements-principles/<br> <br>
https://zizzogroup.com/blog/7-principles-of-design/<br> <br>
https://www.groovecommerce.com/ecommerce-blog/ecommerce-design-principles/<br> <br>

https://webdesign.tutsplus.com/articles/an-introduction-to-color-theory-for-web-designers--webdesign-1437<br> <br> samt
<br> <br>
https://www.trajectorywebdesign.com/blog/web-design-color-psychology/#:~:text=Yellow%20is%20fun%20and%20playful,and%20overwhelming%20in%20larger%20amounts.</p>

<h2> Gruppmedlemmar</h2>

<p>Adrian Dedorson - adde22, Gloria Palm - glpa22</p>
