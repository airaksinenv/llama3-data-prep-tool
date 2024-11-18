# Llama3 datan esikäsittelytyökalu
Valtteri Airaksinen TTV20SAI

---

### Virtuaaliympäristön luonti ja käyttö

Virtuaaliympäristön luonti:

`python -m venv llama`

Ympäristön käyttöönotto:

`source llama/Scripts/activate`

Pakettien lataaminen:

`pip install -r requirements.txt`

Ympäristön käytöstä poisto:

`deactivate`

---

### Ollaman käyttö

Käynnistys:

`ollama serve`

Haetaan mallit:

Avaa uusi terminaali -> Ota ympäristö käyttöön

Nyt voit valita minkä mallin haluat ja noutaa sen esimerkiksi komennolla `ollama pull llama3.2:3b`

Malleja:

`llama3.2:1b` - 1.3GB

`llama3.2:3b` - 2GB

`llama3.1:8b` - 4.7GB

`llama3.1:70b` - 40GB

`llama3.1:405b` - 229GB

`llama3:8b` - 4.7GB

`llama3:70b` - 40GB

Jos mallia ei spesifioi, noudetaan tuorein malli esim `llama3.2` -> `llama3.2:3b`

Näytä ladatut mallit:

`ollama list`

---

### Suomenkielen ymmärrys

##### Kysymys: Ymmärrätkö jos annan sinulle käsiteltäväksi suomenkielistä dataa jonka haluan sinun jaoittelevan?


`llama3.2:1b`
Ehko, en ole yhtynyt kyseessä olevaan suomen kielen ja taidetta koskevaan tuotannoon. Tietoa on ainoastaan sijoiteltu lähemmäs sinua kuin muille joutuneille.

Tietoja ei ole vielä saatavilla, mutta oletettavasti voisin tarkistaa tietoa sitten kunhan käynnistyisi tehtäviä tai pyrkimyksiä. (14.5s)


`llama3.2:3b` 
Olen valmis käsittelemään suomenkielistä dataa! Olen koulutettu käsitelleämään erilaisia kieli- ja tekniikkatekijoita, mutta varsinkin suomalaisen kielen ja sen käyttöjärjestelmien ymmärrystä on olemassa vaikeuksia.

Käytän aina kielitietokantoja tai -tietoa esimerkiksi Wikipedia-sta, Valtion tutustumislainausverkkon tiedostoista, tai muuta luottavaa lähteerää. Kun sinulla on suomenkielinen data, olen valmis käsittelemään sitä.

Onko dataa kosketus- tai teksti-tyyppinen? Mikä on tarkoitusta? (28.6s)


`llama3:8b` 
Hei!

Kyseessä on suomalainen chatbot, joka on valmiina vastaanottamaan ja käsittämään suomenkielisiä tilastotietoja. Olen rakennettu oppimaan jaymmärtämään erilaisia kieliä, myös suomea.

Kuten haluat, anna minulle käsiteltäväksi suomenkielistä dataa, ja minä yritän tehdä siitä järkevää. Olkoon tietoa miten hyvin minä kykenen käsittämään sen! (46.2s)