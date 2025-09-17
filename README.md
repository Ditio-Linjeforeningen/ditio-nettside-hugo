
### For å endre på content
Gå til [content mappen](content) og så den mappen som er for den delen av nettsiden man skal legge til noe.
Der er hver artikkel/post en egen `.md` fil, som er en markdown fil.\
Se [example filen under hendelser](content/arrangementer/example.md) for noen eksempler på options i starten av posten.


### For å kjøre denne nettsiden lokal
For nå så kan man ikke kjøre denne, da det er ikke noe domene som er tilgjenglig.  


følg nedlastningsguiden til [hugo](https://gohugo.io/installation/)

hvis alt går etter planen så er det bare i terminalen: 

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


For noen spørsmål, det er bare å pinge på discord (wiigen eller Mihle), så skal jeg se om jeg kan hjelpe så fort jeg kan!

for nå så bruker jeg MIT lisence, dette må kanskje endre seg

### Annen info
[Layoyts](layouts) mappen er custom layouts som overrides de i temaet.\
[Static](static) mappen overrider temaets css eller legger til.\
[Public](public) mappen er der siden genereres til, trenger vanligvis ikke røres men mapper som endrer navn osv kan bli liggende der.\
Commite endringer til mapper under theme, eks "console" kan skape problemer. Sørg for du vet veien tilbake eller ikke gjør det.

### Andre Temaer som var considered:
[Terminal](https://github.com/panr/hugo-theme-terminal?tab=readme-ov-file)\
[PaperMod](https://themes.gohugo.io/themes/hugo-papermod/)\
[Hugoplate](https://themes.gohugo.io/themes/hugoplate/)

Alternativt 11ty istedenfor HUGO.
Mere custom nettside kan vurderes.