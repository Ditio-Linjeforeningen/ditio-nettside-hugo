# Ditio sin første nettside, lagd med hugo static site generator.
Gjør det lett å legge til events og endre tekst uten å måtte eks skrive HTML, trenger bare å skrive markdown istedenfor. 
Og så tar hugo med GitHub Action seg av å konvertere det til HTML.

Siden er bare ment som et stop intill det er ordnet noe bedre.

## For å endre på content
Gå til [content mappen](content) og så den mappen som er for den delen av nettsiden man skal legge til noe.
Der er hver artikkel/post en egen `.md` fil, som er en markdown fil med "Front matter" mellom `---` på toppen av filen\
Se [example filen under hendelser](content/arrangementer/example.md) for noen eksempler på options i starten av posten.

### Eksempel: Hvordan legge til event

1. Lag en ny branch fra master/main for arrangementet.
2. Legg bilde man vil ha på eventet under `content/img/events`. 
   * Gi den en passende navn. Starte med dato slik at den er sortert er fint. Eks `2026-06-grilling.png`.
3. I `content/arrangementer`, copy paste et tidligere arrangement eller `example.md`
   * Gi den et passende navn, Starte med dato slik at den er sortert er fint. (Påvirker ikke rekkefølge på nettsiden)
4. Endre filen ved å oppdatere innholdet til det man vil ha, se gjerne på tidligere event/`example.md` for inspirasjon.
   * Endre på det som er mellom `---`, det heter "Front matter".

     | Field       | Beskrivelse                                                                                                                                                                                       |
     |-------------|---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
     | title       | Tittelen til arrangementet som vises på siden.                                                                                                                                                    |
     | description | Kort beskrivelse av arrangementet, for søkemotorer osv.                                                                                                                                           |
     | date        | Datoen som nettsiden vil si at eventen er. På formatet `2026-02-26T17:00:00+02:00`. Per da dette ble skrevet, vises ikke tiden på nettsiden, men brukes til sortering hvis flere er på samme dag. |
     | publishDate | Datoen arrangementet blir synlig etter GitHub action blir kjørt. Aka hvis GitHub action kjører og denne datoen ikke er i fortid, vil ikke eventen blir tatt med. På formatet `yyyy-mm-dd`.        |
     | draft       | Hvis satt til true, vil GitHub action ignorere å generere filen til html.                                                                                                                         |
     | slug        | Shortening the URL, nyttig hvis filnavnet er langt. vanligvis brukes filnavnet, men `slug: "en-slug"` vil gjøre at url blir `ditio.org/arrangementer/en-slug/` istedenfor.                        |

   * Legg inn/endre link til bilde etter ---, eks 
     ```md
     ![Bilde Alt tekst](/img/events/2026-06-grilling.png)
     ``` 
     * Det er OK hvis bilde ikke vises i din IDE/editor.
     * Anbefaler at bildet er landskap format, ca sånn som tidligere arrangementer.
   * Legg til teksten som skal være på arrangementet. 
     * Husk at det er markdown, så # for titler, og enten tom linje eller \ på slutten av linjen for ny linje.
   * Velg hvor `<!--more-->` skal være. 
     * Den bestemmer hva som vises på forsiden vs hva som vises når man trykker seg inn på arrangementet. 
       Aka det som er over vises på forsiden, mens både det som er over og under vises når man trykker seg inn.
5. Push branch til GitHub og lag PR.
6. Få PR godkjent/merged, admin kan bypass på godkjenning regler.
7. Vent for GitHub action til å kjøre å publisere det. Burde ta kort tid

## For å kjøre denne nettsiden lokal
Trenger kun å gjøres hvis man vil se hvordan den ser ut uten å pushe til main/master.

Følg nedlastningsguiden til [hugo](https://gohugo.io/installation/)

Hvis alt går etter planen så er det bare i terminalen: 

```bash
git clone https://github.com/Ditio-Linjeforening/d.it-i-o-hugo.git 
cd d.it-i-o-hugo
hugo server
```

Hvis et tema ikke lastes inn lokalt slik det skal, kjør
```bash
git submodule update
git submodule init
```
Og muligens restart IDE

For noen spørsmål, det er bare å pinge på discord (Mihle), så skal jeg se om jeg kan hjelpe så fort jeg kan!

for nå så bruker dette MIT licence.

### Annen info
[Layoyts](layouts) mappen er custom layouts som overrides de i temaet.\
[Static](static) mappen overrider temaets css eller legger til mere.\
[Public](public) mappen er der siden genereres til, trenger vanligvis ikke røres kan fylles opp med gamle ting Github actions/pages bruker ikke denne så er i .gitignore.\
Commite endringer til mapper under theme, eks "console" kan skape problemer. Sørg for du vet veien tilbake eller ikke gjør det.

### Andre Temaer som var considered:
[Terminal](https://github.com/panr/hugo-theme-terminal?tab=readme-ov-file)\
[PaperMod](https://themes.gohugo.io/themes/hugo-papermod/)\
[Hugoplate](https://themes.gohugo.io/themes/hugoplate/)

Alternativt 11ty istedenfor HUGO. Hvis man vil ha noe lignende men anderledes.
Denne siden burde byttes ut med noe mere custom etterhvert.