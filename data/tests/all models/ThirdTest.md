### Kolmas testi

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

        Here are all maalaji's:
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

        These are the different multavuus values:
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
        There can also be just a single value like "Valio Carbo nurmiseos"

        Nurmen ikä is often a number and v or vuosi close to word nurmi, for example 2 v. nurmi. In this case:
            Nurmen ikä: 2v
        """
---

`llama3.2:1b`

rivi  1

Input text: 3 v. nurmi. 70 kg  N/ha. Ei lietettä eikä täydennyskylvetty.  Valio Carbo nurmiseos.

Extracted Data: Here is the extracted information in the format you requested:

Maalaji: Maalaji
Multavuus: Multavuus
ph: pH
Nurmen ikä: Nurmen ikä
Mitä viljellään: Mitä viljellään

* Maalaji: AS aitosavi, BCt ruskosammalsaraturve, CSt sararahkaturve, Ct saraturve, He hiue, HeS hiuesavi, HHk hieno hiekka, HkMr hiekka moreeni, Hs hiesu, HsMr hiesumoreeni, HsS hiesusavi, Ht hieta, HtMr hietamoreeni, HtS hietasavi, Jm järvimuta, KHk karkea hiekka, KHt karkea hieta, LCt metsäsaraturve, Lj lieju, LjS liejusavi urpasavi, LSt metsärahkaturve, Mm multamaa, Mt muta, SCt rahkasaraturve, SMr savimoreeni, Sr soramoreeni, St rahkaturve

Multavuus: 
* vm vähämultainen
* m multava
* rm runsasmultainen
* erm erittäin runsasmultainen
* Mm multamaa

Nurmen ikä:
* 2v Nurmen ikä

rivi  2

Input text: Koulutila. TT 80%, NN 20%. Lannoitus 14.5. YaraMila Y3 400 kg/ha. Maalaji HHt pH 6,2. 3v. nurmi

Extracted Data: Here is the extracted information in the required format:

Maalaji: HHt pH 6,2. 3v.
Multavuus: rm Runsasmultainen
pH: Ht Mr Hieta
Nurmen ikä: 2 v.
Mitä viljellään: TT Tuure 35,5%, TT Rhonia 24,5%, RN Karolina 5%, Engl.rh Riikka10%, PA Saija 7,5%, VA Silvester 2,5%

Multavuus can be close to maalaji written together with it, for example rmHtMr.
Mitä viljellään: HHk Mr Hieta Hietamoreeni
 Multavuus: rm Runsasmultainen

rivi  3

Input text: 2 v. nurmi. HiueS. Ei lietetttä keväällä. Salpietari määrä?  Carbo 3 niiton seos TT Rubinia 35%+ Uula 15%,  RuoN Karolina 20%, NN Valtteri/Evertti 15% + apiloita

Extracted Data: Here is the extracted information in the requested format:

- Maalaji: [AS aitosavi]
- Multavuus: [HeS hiuesavi]
- pH: [HkMr hiekka moreeni]
- Nurmen ikä: [2 v. nurmi]
- Mitä viljellään:
  - TT Tuure (35,5%)
  - TT Rhonia (24,5%)
  - NN Klaara (15%)
  - RN Karolina (5%)
  - Engl.rh Riikka10% (8,5%)
  - PA Saija (7,5%)
  - VA Silvester (2,5%)
- Nurmen ikä: [2 v. nurmi]
 
- Mitä viljellään:
  - HeS hiuesavi
  - HkMr hiekka moreeni
  - HsMr hiesumoreeni
  - HsS  hiesusavi

rivi  4

Input text: TT Nuutti 60 %, NN Kasper 17 %, engl.rh. Riikka 10 %, Koiranheinä 3 %, PA Betty ja AA Frida yht. 10 %. Lannoitus 8.5. Yara Y3 430 kg/ha. Maalaji Ct. 2v. nurmi

Extracted Data: Here is the extracted information in the specified format:

- Maalaji: AS aitosavi
- Multavuus: hm
- pH: m
- Nurmen ikä: 2v
- Mitä viljellään: AA Frida ja Yara Y3 430 kg/ha, CT Ct. 2v, nurmi

- Multavuus can be close to maalaji written together with it, for example rmHtMr.
- Maalaji: HtMr Hietamoreeni
- Multavuus: rm Runsasmultainen

rivi  5

Input text: TT Nuutti 60 %, NN Kasper 17 %, engl.rh. Riikka 10 %, Koiranheinä 3 %, PA Betty ja AA Frida yht. 10 %. Lannoitus 8.5. Yara Y4 470 kg/ha. Maalaji rmHtMr. 1v. nurmi

Extracted Data: Here is the output in the requested format:

Maalaji: [extracted Maalaji]
Multavuus: [extracted Multavuus]
pH: [extracted pH]
Nurmen ikä: [extracted Nurmen ikä]
Mitä viljellään: [extracted Mitä viljellään]

Maalaji:
- 60
- rmHtMr. 1v.
- nurmi

Multavuus:
- vm    vähämultainen  
- m     multava  
- rm    runsasmultainen  
- erm   erittäin runsasmultainen  
- Mm    multamaa  

pH: [extracted pH]
- 6.3

Nurmen ikä:
- 2v

Mitä viljellään:
- Yara Y4 470 kg/ha.
- Pa Betty ja AA Frida yht. 10 %. Lannoitus 8.5.

---

`llama3.2:3b`

rivi  1

Input text: 3 v. nurmi. 70 kg  N/ha. Ei lietettä eikä täydennyskylvetty.  Valio Carbo nurmiseos.

Extracted Data: Based on the provided text and information, I was able to extract the following:

Maalaji: Multavuus
Multavuus: rm Runsasmultainen
pH: ei jätettä eikä täydennyskylvetty = pH ei ole näkyvää (ei jätettä eikä täydennyskylvetty on mahdollinen, mutta se ei ole tärkeää tässä tekstissä)
Nurmen ikä: 3 v. nurmi
Mitä viljellään:
TT Tuure 35,5%, TT Rhonia 24,5%, NN Klaara 15%, RN Karolina 5%, Engl.rh Riikka10%, PA Saija 7,5%, VA Silvester 2,5%

rivi  2

Input text: Koulutila. TT 80%, NN 20%. Lannoitus 14.5. YaraMila Y3 400 kg/ha. Maalaji HHt pH 6,2. 3v. nurmi

Extracted Data: Based on the provided text and information, here are the extracted values:

Maalaji: HHt hieno hieta
Multavuus: rm Runsasmultainen (close to mm Mm multamaa)
ph: 6.2
Nurmen ikä: 3v
Mitä viljellään: TT Tuure 20%, NN Klaara 15%

rivi  3

Input text: 2 v. nurmi. HiueS. Ei lietetttä keväällä. Salpietari määrä?  Carbo 3 niiton seos TT Rubinia 35%+ Uula 15%,  RuoN Karolina 20%, NN Valtteri/Evertti 15% + apiloita

Extracted Data: Here is the extracted information in the requested format:

Maalaji: HtMr hietamoreeni
Multavuus: rm Runsasmultainen
ph: (Not mentioned)
Nurmen ikä: 2v
Mitä viljellään: TT Rubinia 35%, Uula 15%, RuoN Karolina 20%, NN Valtteri/Evertti 15% + apiloita

rivi  4

Input text: TT Nuutti 60 %, NN Kasper 17 %, engl.rh. Riikka 10 %, Koiranheinä 3 %, PA Betty ja AA Frida yht. 10 %. Lannoitus 8.5. Yara Y3 430 kg/ha. Maalaji Ct. 2v. nurmi

Extracted Data: Based on the provided text and information, here are the extracted values in the requested format:

Maalaji: Ct Saraturve
Multavuus: rm Runsasmultainen
pH: (Not explicitly mentioned)
Nurmen ikä: 8.5 v.
Mitä viljellään: Yara Y3 430 kg/ha, PA Betty ja AA Frida yht., TT Nuutti, NN Kasper, engl.rh. Riikka

rivi  5

Input text: TT Nuutti 60 %, NN Kasper 17 %, engl.rh. Riikka 10 %, Koiranheinä 3 %, PA Betty ja AA Frida yht. 10 %. Lannoitus 8.5. Yara Y4 470 kg/ha. Maalaji rmHtMr. 1v. nurmi

Extracted Data: Here is the extracted information in the requested format:

Maalaji: HtMr Hietamoreeni
Multavuus: rm Runsasmultainen
pH: (not mentioned in the text)
Nurmen ikä: 1v
Mitä viljellään: Yara Y4 470 kg/ha

---

`llama3.1:8b`

rivi  1

Input text: 3 v. nurmi. 70 kg  N/ha. Ei lietettä eikä täydennyskylvetty.  Valio Carbo nurmiseos.

Extracted Data: Here are the extracted information in the requested format:

Maalaji: Not specified (no maalaji code is mentioned in the text)

Multavuus: Not specified (no multavuus value is mentioned in the text)

pH: Not specified (pH value is not mentioned in the text)

Nurmen ikä: 3 v. nurmi

Mitä viljellään: Valio Carbo nurmiseos

rivi  2

Input text: Koulutila. TT 80%, NN 20%. Lannoitus 14.5. YaraMila Y3 400 kg/ha. Maalaji HHt pH 6,2. 3v. nurmi

Extracted Data: Here are the extracted values in the requested format:

Maalaji: HHt
Multavuus: (not mentioned)
ph: 6,2
Nurmen ikä: 3v
Mitä viljellään: (not mentioned)

rivi  3

Input text: 2 v. nurmi. HiueS. Ei lietetttä keväällä. Salpietari määrä?  Carbo 3 niiton seos TT Rubinia 35%+ Uula 15%,  RuoN Karolina 20%, NN Valtteri/Evertti 15% + apiloita

Extracted Data: Here are the extracted information in the format you requested:

Maalaji: HeS Hiuesavi (assuming "HiueS" is a combination of maalaji and multavuus, similar to "rmHtMr")

Multavuus: HeS Vähämultainen (since "HeS" is written together with "HiueS", it's likely that the multavuus value is "vm" or "vähämultainen")

pH: Not specified in the text

Nurmen ikä: 2v (nurmi means field, and "2 v." suggests that the age of the field is 2 years)

Mitä viljellään: Carbo 3 niiton seos TT Rubinia 35%, Uula 15%, RuoN Karolina 20%, NN Valtteri/Evertti 15% + apiloita (this suggests that the crops being grown in the field are a mix of different varieties, with percentages indicating their proportion)

rivi  4

Input text: TT Nuutti 60 %, NN Kasper 17 %, engl.rh. Riikka 10 %, Koiranheinä 3 %, PA Betty ja AA Frida yht. 10 %. Lannoitus 8.5. Yara Y3 430 kg/ha. Maalaji Ct. 2v. nurmi

Extracted Data: Based on the provided text:

Maalaji: Ct 2v. nurmi
Multavuus: (not specified)
pH: (not specified)
Nurmen ikä: 2v
Mitä viljellään: TT Nuutti 60 %, NN Kasper 17 %, Engl.rh. Riikka 10 %, Koiranheinä 3 %, PA Betty ja AA Frida yht. 10 %

rivi  5

Input text: TT Nuutti 60 %, NN Kasper 17 %, engl.rh. Riikka 10 %, Koiranheinä 3 %, PA Betty ja AA Frida yht. 10 %. Lannoitus 8.5. Yara Y4 470 kg/ha. Maalaji rmHtMr. 1v. nurmi

Extracted Data: Based on the provided text, here are the extracted information:

Maalaji: rmHtMr

Multavuus: rm (Runsasmultainen)

ph: Not mentioned in the text

Nurmen ikä: 1v. nurmi

Mitä viljellään: Lannoitus (Fertilizer) with a rate of 8.5, and Yara Y4 with a rate of 470 kg/ha, and it's mentioned that Koiranheinä is grown in the field with a percentage of 3%.