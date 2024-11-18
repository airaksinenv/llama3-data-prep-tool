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


### Ensimmäinen testi

---

`llama3.2:1b`


1

Input text: 3 v. nurmi. 70 kg  N/ha. Ei lietettä eikä täydennyskylvetty.  Valio Carbo nurmiseos.
Extracted Data: Hei, teitä tarkastellaan lähtökohtaisesti tekstin:

* Maalaji: Maalaji
* Multavuus: Ei lietettä eikä täydennyskylvetty.
* Nurmen ikä: Nurmen ikä (se on määritelty 70 kg N/ha)
* Mitä viljellään: Viljely

Tämän tekstin sivuillemme.

2

Input text: Koulutila. TT 80%, NN 20%. Lannoitus 14.5. YaraMila Y3 400 kg/ha. Maalaji HHt pH 6,2. 3v. nurmi
Extracted Data: Kun koodin tulee käyttää yleissähäisillä äänimikoilla, on tarvittava antaa hänen käytetysti luetteloon nimeltä, mitä tehdäksesi ja mitä lopputulossasi. Tämä tapauksessa olette hyväkseen päättämään niiden, joita seuraavat tekstissä mainitaan.

- Maalaji
  - [ extracted maalaji ]
- Multavuus
  - [ extracted multavuus ]
- Nurmen ikä
  - [ extracted nurmen ikä ]
- Mitä viljellään
  - [ extracted mitä viljellään ]

3

Input text: 2 v. nurmi. HiueS. Ei lietetttä keväällä. Salpietari määrä?  Carbo 3 niiton seos TT Rubinia 35%+ Uula 15%,  RuoN Karolina 20%, NN Valtteri/Evertti 15% + apiloita
Extracted Data: Hei, tämä puhui Finnish ruhtinasta:

- Maalaji: Maalaji (maali)
- Multavuus: Multavuus
- Nurmen ikä: Nurmen ikä (ikä)
- Mitä viljellään: Viljellään (viljellää)

Tämä on tämän ruhtinan maailman lajuimmat lihat, joka elää nurminmaan.

4

Input text: TT Nuutti 60 %, NN Kasper 17 %, engl.rh. Riikka 10 %, Koiranheinä 3 %, PA Betty ja AA Frida yht. 10 %. Lannoitus 8.5. Yara Y3 430 kg/ha. Maalaji Ct. 2v. nurmi
Extracted Data: Hei! Tämän tekstin avaimena ovat seuraavat tietoja:
- Maalaji: 60 %
- Multavuus: 17 %
- Nurmen ikä: 3-vuotias
- Mitä viljellään: viljelysruoka

5

Input text: TT Nuutti 60 %, NN Kasper 17 %, engl.rh. Riikka 10 %, Koiranheinä 3 %, PA Betty ja AA Frida yht. 10 %. Lannoitus 8.5. Yara Y4 470 kg/ha. Maalaji rmHtMr. 1v. nurmi
Extracted Data: Maalaji: 
Multavuus:
Nurmen ikä:
Mitä viljellään:

TT Nuutti
- Maalaji: 60 % (rmHtMr. 1v.)
- Multavuus: 20%
- Nurmen ikä: 4 vuotta
- Mitä viljellään: Koiranheinä

---

`llama3.2:3b`


1

Input text: 3 v. nurmi. 70 kg  N/ha. Ei lietettä eikä täydennyskylvetty.  Valio Carbo nurmiseos.
Extracted Data: I'd be happy to help you extract the information. However, I don't see any text in Finnish. Could you please provide the text in Finnish, and I'll do my best to extract the requested information?

2

Input text: Koulutila. TT 80%, NN 20%. Lannoitus 14.5. YaraMila Y3 400 kg/ha. Maalaji HHt pH 6,2. 3v. nurmi
Extracted Data: Here is the extracted information in the requested format:

Maalaji: HHt
Multavuus: pH 6,2
Nurmen ikä: 3v.
Mitä viljellään: TT (TT 80%) ja NN (NN 20%)

3

Input text: 2 v. nurmi. HiueS. Ei lietetttä keväällä. Salpietari määrä?  Carbo 3 niiton seos TT Rubinia 35%+ Uula 15%,  RuoN Karolina 20%, NN Valtteri/Evertti 15% + apiloita
Extracted Data: I'd be happy to help you extract the information from the text. However, I don't see any text in Finnish. Could you please provide the text in Finnish, and I'll do my best to extract the requested information for you?

If you don't have the text available, I can try to help you translate it into English so we can proceed with extracting the information.

Once you provide the text or its translation, I'll be happy to assist you!

4

Input text: TT Nuutti 60 %, NN Kasper 17 %, engl.rh. Riikka 10 %, Koiranheinä 3 %, PA Betty ja AA Frida yht. 10 %. Lannoitus 8.5. Yara Y3 430 kg/ha. Maalaji Ct. 2v. nurmi
Extracted Data: I'd be happy to help you extract the information. However, I don't see the text in Finnish. Please provide the text, and I'll do my best to extract the requested information.

If you provide the text, I'll format the output as follows:

Maalaji: [extracted maalaji]
Multavuus: [extracted multavuus]
Nurmen ikä: [extracted nurmen ikä]
Mitä viljellään: [extracted mitä viljellään]

Please paste the text in Finnish, and I'll get started!

5

Input text: TT Nuutti 60 %, NN Kasper 17 %, engl.rh. Riikka 10 %, Koiranheinä 3 %, PA Betty ja AA Frida yht. 10 %. Lannoitus 8.5. Yara Y4 470 kg/ha. Maalaji rmHtMr. 1v. nurmi
Extracted Data: I can try to help you with that. However, I need the text in Finnish for me to extract the information correctly.

Could you please provide the text in Finnish, and I'll be happy to assist you in extracting the required information?

---

`llama3.1:8b`


1

Input text: 3 v. nurmi. 70 kg  N/ha. Ei lietettä eikä täydennyskylvetty.  Valio Carbo nurmiseos.
Extracted Data: I'll do my best to extract the information from the text. Since I don't understand Finnish, I might make mistakes. Please correct me if needed!

Here are the extracted values:

Maalaji: Valio Carbo nurmiseos (it seems like a type of grass or fertilizer)

Multavuus: Not mentioned explicitly

pH: Not mentioned

Nurmen ikä: 3 v. (three years old, I assume this is the age of the meadow)

Mitä viljellään: Not mentioned explicitly

2

Input text: Koulutila. TT 80%, NN 20%. Lannoitus 14.5. YaraMila Y3 400 kg/ha. Maalaji HHt pH 6,2. 3v. nurmi
Extracted Data: I can help you with that!

The text is in Finnish, and I'll extract the information you requested. Here's the output:

Maalaji: HHt
Multavuus: (not mentioned)
pH: 6,2
Nurmen ikä: 3v.
Mitä viljellään: nurmi

3

Input text: 2 v. nurmi. HiueS. Ei lietetttä keväällä. Salpietari määrä?  Carbo 3 niiton seos TT Rubinia 35%+ Uula 15%,  RuoN Karolina 20%, NN Valtteri/Evertti 15% + apiloita
Extracted Data: I'd be happy to help you with that! However, I need to point out that the text is in Finnish and my understanding of the language is limited. Nevertheless, based on my analysis, here's what I was able to extract:

Maalaji: HiueS (likely a type of grass or meadow)

Multavuus: Not explicitly mentioned

pH: Not mentioned

Nurmen ikä: 2 v. (likely means "the age of the meadow" and "v." stands for "vuosi," which is Finnish for "year")

Mitä viljellään: Not explicitly mentioned, but based on the context, it seems like something related to what's being cultivated or grown in the meadow (perhaps a type of grass or crop).

Please note that my understanding may not be entirely accurate due to language limitations. If you could provide more context or clarify any unclear terms, I'd be happy to try again!

4

Input text: TT Nuutti 60 %, NN Kasper 17 %, engl.rh. Riikka 10 %, Koiranheinä 3 %, PA Betty ja AA Frida yht. 10 %. Lannoitus 8.5. Yara Y3 430 kg/ha. Maalaji Ct. 2v. nurmi
Extracted Data: I'd be happy to help! However, I need to note that I'm a large language model, I don't have the capability to read Finnish text directly. But I can try to extract the information you're looking for using translation and pattern recognition.

Here's what I found:

Maalaji: Ct. 2v. nurmi (meaning "cut grass" or "turf" in English)

Multavuus: Not mentioned explicitly, but based on the context, it seems that this is a type of fertilizer application, specifically Yara Y3 with 430 kg/ha rate.

pH: Not mentioned explicitly.

Nurmen ikä: 2v (meaning "two-year-old" in English, likely referring to the age of the turf or grass).

Mitä viljellään: Not mentioned explicitly.

5

Input text: TT Nuutti 60 %, NN Kasper 17 %, engl.rh. Riikka 10 %, Koiranheinä 3 %, PA Betty ja AA Frida yht. 10 %. Lannoitus 8.5. Yara Y4 470 kg/ha. Maalaji rmHtMr. 1v. nurmi
Extracted Data: I'd be happy to help you with that. Here are the extracted information in the requested format:

Maalaji: rmHtMr
Multavuus: Not mentioned in the text (since it's not a measurable parameter)
pH: Not mentioned in the text (since pH values are typically reported as numerical values, which is not present here)

Nurmen ikä: 1v (which translates to "one-year-old" meadow)

Mitä viljellään: Not mentioned in the text (it seems that this text does not contain information about what's being cultivated)

Let me know if you have any further questions!