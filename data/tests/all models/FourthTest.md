### Neljäs testi

        prompt = f"""
        Extract the following information from the text below, the text is in finnish:
        - Maalaji
        - Multavuus
        - pH
        - Nurmen ikä
        - Mitä viljellään

        Text: "{text}"

        Provide the output in this format:
        Maalaji: [extracted maalaji]
        Multavuus: [extracted multavuus]
        ph: [extracted pH]
        Nurmen ikä: [extracted nurmen ikä]
        Mitä viljellään: [extracted mitä viljellään]

        some helpful information:

        Here are all maalaji's, maalaji will always be one of these:
            "AS   aitosavi",
            "BCt  ruskosammalsaraturve",
            "CSt  sararahkaturve",
            "Ct   saraturve",
            "He   hiue",
            "HeS  hiuesavi",
            "HHk  hieno hiekka",
            "HHt  hieno hieta",
            "HkMr hiekka moreeni",
            "Hs   hiesu",
            "HsMr hiesumoreeni",
            "HsS  hiesusavi",
            "Ht   hieta",
            "HtMr hietamoreeni",
            "HtS  hietasavi",
            "Jm   järvimuta",
            "KHk  karkea hiekka",
            "KHt  karkea hieta",
            "LCt  metsäsaraturve",
            "Lj   lieju",
            "LjS  liejusavi, urpasavi",
            "LSt  metsärahkaturve",
            "Mm   multamaa",
            "Mt   muta",
            "SCt  rahkasaraturve",
            "SMr  savimoreeni",
            "Sr   sora",
            "SrMr soramoreeni",
            "St   rahkaturve"

        These are the different multavuus values, multavuus will always be one of these:
            vm    vähämultainen  
            m     multava  
            rm    runsasmultainen  
            erm   erittäin runsasmultainen  
            Mm    multamaa  
            
        Multavuus can be close to maalaji written together with it, for example rmHtMr. In this case:
            Maalaji: HtMr Hietamoreeni
            Multavuus: rm Runsasmultainen
            
        Answer to "Mitä viljellään?" is often a list of items with percentages on how much of them is in the field, for example:
            TT Tuure 35,5%, TT Rhonia 24,5%, NN Klaara 15%, RN Karolina 5%, Engl.rh Riikka10%, PA Saija 7,5%, VA Silvester 2,5%
            Here TT is Timotei, NN is Nurminata, RN is Ruokonata, Engl.rh is Englannin raiheinä, PA is Puna-apila, VA is Valko-apila and AA is Alsike-apila.
            Tuure, Rhonia, Klaara, Karolina, Riikka, Saija & Silvester are the brand names. Brand names might also not be specified for example:
            TT 20%, RN 80%
        There can also be just a single value like "Valio Carbo nurmiseos"

        Nurmen ikä is often a number and v or vuosi close to word nurmi, for example 2 v. nurmi. In this case:
            Nurmen ikä: 2v

        Some of the values we are looking for can be missing or have typos in them.
        """
---

`llama3.2:1b`

rivi  1

Input text: 3 v. nurmi. 70 kg  N/ha. Ei lietettä eikä täydennyskylvetty.  Valio Carbo nurmiseos.

Extracted Data: Here is the extracted information in the specified format:

- Maalaji: AS
- Multavuus: vm
- pH: -
- Nurmen ikä: 70 v
- Mitä viljellään:
 * Tuure: 35,5%
 * Rhonia: 24,5%
 * NN Klaara: 15%
 * RN Karolina: 5%
 * Engl.rh Riikka: 10%
 * PA Saija: 7,5%
 * VA Silvester: 2,5%

- Multavuus can be close to maalaji written together with it:
 
 Maalaji: HtMr Hietamoreeni
 Multavuus: rm Runsasmultainen

- Mitä viljellään:

 TT Tuure 35,5%, TT Rhonia 24,5%, NN Klaara 15%, RN Karolina 5%, Engl.rh Riikka10%, PA Saija 7,5%, VA Silvester 2,5%

- Nurmen ikä:
 
 Nurmen ikä: 70 v

- Mitä viljellään:

 * Tuure: 35,5%
 * Rhonia: 24,5%
 * Klaara: 15%
 * Karolina: 5%
 * Riikka: 10%
 * Saija: 7,5%

- Multavuus:
 
 VM Vähämultainen
 M Multava
 RM Runsasmultainen
 Erittäin runsasmultainen
 Mm Multamaa

- Nurmen ikä (kaksi vähemmällistä arvoista)

 Nurmen ikä: 70v

rivi  2

Input text: Koulutila. TT 80%, NN 20%. Lannoitus 14.5. YaraMila Y3 400 kg/ha. Maalaji HHt pH 6,2. 3v. nurmi

Extracted Data: Here is the extracted information in the requested format:

Maalaji: [extracted maalaji]
Multavuus: [extracted multavuus]
pH: [extracted pH]
Nurmen ikä: [extracted nurmen ikä]
Mitä viljellään:
- Timotei (TT 80%, NN 20%)
- Karolina (NN 24.5%, RN 15%)
- Riikka10% (Engl.rh 10%)
- Puna-apila (PA 7.5%)
- Valko-apila (VA 2.5%)

Multavuus: [extracted multavuus]
va: HtMr Hietamoreeni
rm: Runsasmultainen
vähämultainen: vm
multava: Mm
runsasmultainen: erm
erittäin runsasmultainen: erm

Nurmen ikä: 2v

rivi  3

Input text: 2 v. nurmi. HiueS. Ei lietetttä keväällä. Salpietari määrä?  Carbo 3 niiton seos TT Rubinia 35%+ Uula 15%,  RuoN Karolina 20%, NN Valtteri/Evertti 15% + apiloita

Extracted Data: Maalaji: [AS aitosavi]
Multavuus: [vm Runsasmultainen]
pH: [p Hidroklimateen pH]
Nurmen ikä: [2v]
Mitä viljellään: [TT Rubinia 35%+ Uula 15%, RuoN Karolina 20%, NN Valtteri/Evertti 15% + apiloita]

Multavuus: 
- m (multa)
- rm (runsas)
- erm (erittäin runsas)
- Mm (multamaa)

pH: [p Hidroklimateen pH]
- vähämultainen (vähän multainen)
- multava (multaa)
- runsasmultainen (runsas)
- erittäin runsasmultainen (erittäin runsas)

Nurmen ikä: 
- 2v (2 vuotta)

Mitä viljellään:
- TT Rubinia
- Uula
- RuoN Karolina
- NN Valtteri/Evertti
- RN Karolina
- Engl.rh Riikka10%
- PA Saija 7,5%
- VA Silvester 2,5%

Multavuus: 
- rm Runsasmultainen

Nurmen ikä:
- 2v (2 vuotta)

Mitä viljellään:
- TT Tuure
- NN Klaara
- RN Karolina
- Engl.rh Riikka
- PA Saija & Silvester

rivi  4

Input text: TT Nuutti 60 %, NN Kasper 17 %, engl.rh. Riikka 10 %, Koiranheinä 3 %, PA Betty ja AA Frida yht. 10 %. Lannoitus 8.5. Yara Y3 430 kg/ha. Maalaji Ct. 2v. nurmi

Extracted Data: Maalaji: [AS aitosavi]
Multavuus: [He hiue]
pH: [SCt rahkasaraturve]
Nurmen ikä: [2v nurmi]
Mitä viljellään:
TT 60 %, NN Kasper 17 %, engl.rh Riikka 10 %, Koiranheinä 3 %, PA Betty ja AA Frida yht. 10 %.

rivi  5

Input text: TT Nuutti 60 %, NN Kasper 17 %, engl.rh. Riikka 10 %, Koiranheinä 3 %, PA Betty ja AA Frida yht. 10 %. Lannoitus 8.5. Yara Y4 470 kg/ha. Maalaji rmHtMr. 1v. nurmi

Extracted Data: Maalaji: [extracted maalaji]
Multavuus: [extracted multavuus]
pH: [extracted pH]
Nurmen ikä: [extracted nurmen ikä]
Mitä viljellään: [extracted mitä viljellään]

* Maalaji:
+ AS aitosavi
+ BCt ruskosammalsaraturve
+ CSt sararahkaturve
+ Ct saraturve
+ He hiue
+ HeS hiuesavi
+ HHk hieno hiekka
+ HHt hieno hieta
+ HkMr hiekka moreeni
+ Hs hiesu
+ HsMr hiesumoreeni
+ HsS hiesusavi
+ Ht hieta
+ HtMr hietamoreeni
+ HtS hietasavi
+ Jm järvimuta
+ KHk karkea hiekka
+ KHt karkea hieta
+ LCt metsäsaraturve
+ Lj lieju
+ LjS liejusavi urpasavi
+ LSt metsärahkaturve
+ Mm multamaa
+ Mt muta
+ SCt rahkasaraturve
+ SMr savimoreeni
+ Sr sora
+ SrMr soramoreeni
+ St rahkaturve

* Multavuus:
 + vm vähämultainen  
 + m multava  
 + rm runsasmultainen  
 + erm erittäin runsasmultainen  
 + Mm multamaa  

* pH: [extracted pH]
* Nurmen ikä: 2v
* Mitä viljellään: Lieju

Nota, että virheen saaneiden kaavien mukaan mitä viljellään on esitetty lyhyesti, muut tietotiedot ovat vakiintuneita tai epäviraisia.

---

`llama3.2:3b`

rivi  1

Input text: 3 v. nurmi. 70 kg  N/ha. Ei lietettä eikä täydennyskylvetty.  Valio Carbo nurmiseos.

Extracted Data: Based on the provided information, I was unable to extract the requested data from the original text. However, I can help you identify some possible errors or omissions.

The original text contains:

* "3 v. nurmi." (Missing year value)
* "70 kg  N/ha." (No clear connection between kg and N/ha; possibly a typo?)
* "Ei lietettä eikä täydennyskylvetty." (Nothing relevant to the requested data)
* "Valio Carbo nurmiseos." (Possible error, as it seems like a product name rather than a mix of maalaji and multavuus)

Assuming there's more context or information about the text, I can try to provide more help.

Please note that without additional context or corrections to the original text, I couldn't extract the exact values you requested.

rivi  2

Input text: Koulutila. TT 80%, NN 20%. Lannoitus 14.5. YaraMila Y3 400 kg/ha. Maalaji HHt pH 6,2. 3v. nurmi

Extracted Data: Here is the extracted information:

Maalaji: HHt Hieno hieta
Multavuus: rm Runsasmultainen
pH: 6,2
Nurmen ikä: 3v
Mitä viljellään: TT Tuure 20%, NN Nurminata 20%, RN Ruokonata 80%

rivi  3

Input text: 2 v. nurmi. HiueS. Ei lietetttä keväällä. Salpietari määrä?  Carbo 3 niiton seos TT Rubinia 35%+ Uula 15%,  RuoN Karolina 20%, NN Valtteri/Evertti 15% + apiloita

Extracted Data: Based on the provided text, I was unable to extract all the information due to errors and unclear text in Finnish. However, here is what I could manage:

 Maalaji: HeS Hiuesavi
 Multavuus: m Multava
 pH: (Not specified)
 Nurmen ikä: 2 v. nurmi
 Mitä viljellään: TT Rubinia 35%, Uula 15%, RuoN Karolina 20%, NN Valtteri/Evertti 15%

rivi  4

Input text: TT Nuutti 60 %, NN Kasper 17 %, engl.rh. Riikka 10 %, Koiranheinä 3 %, PA Betty ja AA Frida yht. 10 %. Lannoitus 8.5. Yara Y3 430 kg/ha. Maalaji Ct. 2v. nurmi

Extracted Data: Based on the provided text, I was able to extract the following information:

* Maalaji: Ct. (Ct. 2v.)
* Multavuus: m (Mm multamaa)
* pH: Unfortunately, the pH value is not explicitly mentioned in the text.
* Nurmen ikä: 2 v. nurmi
* Mitä viljellään: TT Nuutti 60 %, NN Kasper 17 %, Engl.rh Riikka 10 %, Koiranheinä 3 %, PA Betty ja AA Frida yht. 10 %.

rivi  5

Input text: TT Nuutti 60 %, NN Kasper 17 %, engl.rh. Riikka 10 %, Koiranheinä 3 %, PA Betty ja AA Frida yht. 10 %. Lannoitus 8.5. Yara Y4 470 kg/ha. Maalaji rmHtMr. 1v. nurmi

Extracted Data: Based on the provided text and information, here is the 
extracted data in the requested format:

Maalaji: HtMr
Multavuus: rm
pH: (not mentioned)
Nurmen ikä: 2v
Mitä viljellään: TT Nuutti 60 %, NN Kasper 17 %, Engl.rh Riikka 10 %, Koiranheinä 3 %, PA Betty ja AA Frida yht. 10 %

---

`llama3.1:8b`

rivi  1

Input text: 3 v. nurmi. 70 kg  N/ha. Ei lietettä eikä täydennyskylvetty.  Valio Carbo nurmiseos.

Extracted Data: Here is the extracted information:

Maalaji: 3 v. nurmi

Multavuus: Not specified, but based on the format and maalaji, it's likely that Multavuus would be Mm (multamaa) since the soil type is a meadow (nurmi)

pH: Not specified

Nurmen ikä: 2v (two years old)

Mitä viljellään: Valio Carbo nurmiseos

rivi  2

Input text: Koulutila. TT 80%, NN 20%. Lannoitus 14.5. YaraMila Y3 400 kg/ha. Maalaji HHt pH 6,2. 3v. nurmi

Extracted Data: Based on the provided text, here is the extracted information:

Maalaji: HHt
Multavuus: (not specified)
pH: 6.2
Nurmen ikä: 3v
Mitä viljellään: Lannoitus (it seems like "Lannoitus" refers to a fertilizer type, but it's not clear what is being cultivated)

Note that Multavuus value is not specified in the provided text, and Mitä viljellään might be referring to the type of fertilizer used rather than what is being cultivated.

rivi  3

Input text: 2 v. nurmi. HiueS. Ei lietetttä keväällä. Salpietari määrä?  Carbo 3 niiton seos TT Rubinia 35%+ Uula 15%,  RuoN Karolina 20%, NN Valtteri/Evertti 15% + apiloita

Extracted Data: Based on the provided text, I extracted the following information:

Maalaji: HeS HiueSavi

Multavuus: vm Vähämultainen

pH: None mentioned (not present in this specific text)

Nurmen ikä: 2 v. nurmi

Mitä viljellään: Carbo 3 niiton seos TT Rubinia 35%, Uula 15%, RuoN Karolina 20%, NN Valtteri/Evertti 15% + apiloita

rivi  4

Input text: TT Nuutti 60 %, NN Kasper 17 %, engl.rh. Riikka 10 %, Koiranheinä 3 %, PA Betty ja AA Frida yht. 10 %. Lannoitus 8.5. Yara Y3 430 kg/ha. Maalaji Ct. 2v. nurmi

Extracted Data: Based on the provided text, here is the extracted information:

Maalaji: Ct   saraturve

Multavuus: Mm    multamaa

pH: Not mentioned (no pH value found)

Nurmen ikä: 2v nurmi

Mitä viljellään: TT Nuutti 60 %, NN Kasper 17 %, engl.rh. Riikka 10 %, Koiranheinä 3 %, PA Betty ja AA Frida yht. 10 %

rivi  5

Input text: TT Nuutti 60 %, NN Kasper 17 %, engl.rh. Riikka 10 %, Koiranheinä 3 %, PA Betty ja AA Frida yht. 10 %. Lannoitus 8.5. Yara Y4 470 kg/ha. Maalaji rmHtMr. 1v. nurmi

Extracted Data: Based on the provided text:

Maalaji: rmHtMr (hietamoreeni)

Multavuus: rm (runsasmultainen)

pH: Not mentioned

Nurmen ikä: 1v. nurmi (one-year-old meadow)

Mitä viljellään: The cultivation is likely a mix of different species, as the text only mentions "Maalaji" and not specific plant types.
