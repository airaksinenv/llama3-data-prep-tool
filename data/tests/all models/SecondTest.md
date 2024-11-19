### Toinen testi

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

        Multavuus can be close to maalaji:
            vm    vähämultainen  
            m     multava  
            rm    runsasmultainen  
            erm   erittäin runsasmultainen  
            Mm    multamaa  
            
        Answer to "Mitä viljellään?" is often a list of items with percentages on how much of them is in the field
        """
---

`llama3.2:1b`

rivi  1
Input text: 3 v. nurmi. 70 kg  N/ha. Ei lietettä eikä täydennyskylvetty.  Valio Carbo nurmiseos.
Extracted Data: Here is the extracted information in the requested format:

Maalaji: AS   aitosavi 
Multavuus: m     multava  
pH: 6-7  
Nurmen ikä: HeS  hiuesavi 
Mitä viljellään: HkMr hiekka moreeni

rivi  2
Input text: Koulutila. TT 80%, NN 20%. Lannoitus 14.5. YaraMila Y3 400 kg/ha. Maalaji HHt pH 6,2. 3v. nurmi
Extracted Data: Here is the extracted information in the requested format:

Maalaji: [HHt  hieno hieta]
Multavuus: [hieno hiekka, erittäin runsasmultainen]
pH: [6,2]
Nurmen ikä: [heue]
Mitä viljellään:
 
- maalaji
- multavuus
- pH
- nurmen ikä
- mitä viljellään

rivi  3
Input text: 2 v. nurmi. HiueS. Ei lietetttä keväällä. Salpietari määrä?  Carbo 3 niiton seos TT Rubinia 35%+ Uula 15%,  RuoN Karolina 20%, NN Valtteri/Evertti 15% + apiloita
Extracted Data: Here is the extracted information in the requested format:

Maalaji: [AS]
Multavuus: vähämultainen 
Ph: 2
Nurmen ikä:
Mitä viljellään: heieksä

rivi  4
Input text: TT Nuutti 60 %, NN Kasper 17 %, engl.rh. Riikka 10 %, Koiranheinä 3 %, PA Betty ja AA Frida yht. 10 %. Lannoitus 8.5. Yara Y3 430 kg/ha. Maalaji Ct. 2v. nurmi
Extracted Data: Here is the extracted information in the requested format:

- Maalaji: AS aitosavi
- Multavuus: vm vähämultainen
- pH: 8.5
- Nurmen ikä: 60
- Mitä viljellään:
    - Nurmit (HeS, HkMr) : hiue
    - Maalat (HsMr) : hiesumoreeni
    - Karhut (LJ, KHt, LSt) : lieju/liejusavi/rahka hieta

rivi  5
Input text: TT Nuutti 60 %, NN Kasper 17 %, engl.rh. Riikka 10 %, Koiranheinä 3 %, PA Betty ja AA Frida yht. 10 %. Lannoitus 8.5. Yara Y4 470 kg/ha. Maalaji rmHtMr. 1v. nurmi
Extracted Data: Here is the extracted information in the required format:

Maalaji: [AS aitosavi, BCt ruskosammalsaraturve, CSt sararahkaturve, Ct saraturve, He hiue, HeS hiuesavi, HHk hieno hiekka, Hs hiesu, HsMr hiesumoreeni, HsS hiesusavi, Ht hieta, HtMr hietamoreeni, HtS hietasavi, Jm järvimuta, KHk karkea hiekka, KHt karkea hieta, LCt metsäsaraturve, Lj lieju, LjS liejusavi urpasavi, LSt metsärahkaturve, Mm multamaa, Mt muta, SCt rahkasaraturve, SMr savimoreeni, Sr sora, SrMr soramoreeni, St Rahkaturve]
 
 Multavuus: [vm vähämultainen, m multava, rm runsasmultainen, erm erittäin runsasmultainen, Mm multamaa]
 
 pH: 
 
 Nurmen ikä: 70 
 Mitä viljellään:
 
 Lannoitus 8.5. Yara Y4 470 kg/ha.

---

`llama3.2:3b`

rivi  1
Input text: 3 v. nurmi. 70 kg  N/ha. Ei lietettä eikä täydennyskylvetty.  Valio Carbo nurmiseos.
Extracted Data: Based on the provided text and information, here are the extracted values:

* Maalaji: Hs (hiesu)
* Multavuus: rm (runsasmultainen)
* pH: No value given in the text.
* Nurmen ikä: 3 vuotta
* Mitä viljellään: "70 kg N/ha. Ei lietettä eikä täydennyskylvetty. Valio Carbo nurmiseos." translates to "Valio Carbo nurmisoilus".

rivi  2
Input text: Koulutila. TT 80%, NN 20%. Lannoitus 14.5. YaraMila Y3 400 kg/ha. Maalaji HHt pH 6,2. 3v. nurmi
Extracted Data: Based on the provided text and information, here are the extracted values:

 Maalaji: HHt
 Multavuus: m (multava)
 pH: 6.2
 Nurmen ikä: 3v.
 Mitä viljellään:
 - AS: 0% (itosavi)
 - BCt: 0% (ruskosammalsaraturve)
 - CSt: 0% (sararahkaturve)
 - Ct: 0% (saraturve)
 - He: 20% (hiue)
 - HeS: 0% (hiuesavi)
 - HHk: 0% (hieno hiekka)
 - HHt: 80% (hieno hieta)
 - HkMr: 0% (hiiekka moreeni)
 - Hs: 20% (hiesu)
 - HsMr: 0% (hiesumoreeni)
 - HsS: 0% (hiesusavi)
 - Ht: 20% (hieta)
 - HtMr: 0% (hietamoreeni)
 - HtS: 0% (hietasavi)
 - Jm: 0% (järvimuta)
 - KHk: 0% (karkea hiekka)
 - KHt: 0% (karkea hieta)
 - LCt: 0% (metsäsaraturve)
 - Lj: 20% (lieju)
 - LjS: 0% (liejusavi, urpasavi)
 - LSt: 0% (metsärahkaturve)
 - Mm: 80% (multamaa)
 - Mt: 0% (muta)
 - SCt: 20% (rahkasaraturve)
 - SMr: 0% (savimoreeni)
 - Sr: 0% (sora)
 - SrMr: 0% (soramoreeni)
 - St: 0% (rahkaturve)

Please note that the percentages for "Mitä viljellään?" might not add up to 100%, as some values are missing.

rivi  3
Input text: 2 v. nurmi. HiueS. Ei lietetttä keväällä. Salpietari määrä?  Carbo 3 niiton seos TT Rubinia 35%+ Uula 15%,  RuoN Karolina 20%, NN Valtteri/Evertti 15% + apiloita
Extracted Data: Based on the provided text and information, here are the extracted results:

Maalaji: Hieno hiekka (HHk)

Multavuus: runsasmultainen (rm)

pH: ei mainittu erikseen, mutta se on tietysti vähän alkalista vettä

Nurmen ikä: 2 vuotta

Mitä viljellään:
- Carbo 35%
- Uula 15%
- RuoN Karolina 20%
- NN Valtteri/Evertti 15%

rivi  4
Input text: TT Nuutti 60 %, NN Kasper 17 %, engl.rh. Riikka 10 %, Koiranheinä 3 %, PA Betty ja AA Frida yht. 10 %. Lannoitus 8.5. Yara Y3 430 kg/ha. Maalaji Ct. 2v. nurmi
Extracted Data: Based on the provided information, I extracted the following data from the text:


Maalaji: Ct. 2v. nurmi


Multavuus: rm    runsasmultainen (runsasmultainen multava maali)


pH: Not specified


Nurmen ikä: 60 % (TT Nuutti), 17 % (NN Kasper), 10 % (engr. Riikka, PA Betty, AA Frida)


Mitä viljellään:
- vm    vähämultainen 60 %
- m     multava  17%
- erm   erittäin runsasmultainen 10%

rivi  5
Input text: TT Nuutti 60 %, NN Kasper 17 %, engl.rh. Riikka 10 %, Koiranheinä 3 %, PA Betty ja AA Frida yht. 10 %. Lannoitus 8.5. Yara Y4 470 kg/ha. Maalaji rmHtMr. 1v. nurmi
Extracted Data: Based on the provided text and information, here are the extracted values:

Maalaji: hiekka moreeni
Multavuus: m (multava)
pH: ei mainittu (no pH value mentioned)
Nurmen ikä: ei mainittu (no age of Nurmi mentioned)
Mitä viljellään:
- AS aitosavi 60 %
- BCt ruskosammalsaraturve 17 %
- CSt sararahkaturve 10 %
- Koiranheinä 3 %
- PA Betty ja AA Frida yht. 10 %

---

`llama3.1:8b`

rivi  1
Input text: 3 v. nurmi. 70 kg  N/ha. Ei lietettä eikä täydennyskylvetty.  Valio Carbo nurmiseos.
Extracted Data: After analyzing the text, I extracted the following information:

Maalaji: 3 v. nurmi

Multavuus: Mm (multamaa)

pH: Not mentioned in the text

Nurmen ikä: 3 v. (three years old)

Mitä viljellään: Valio Carbo (it's likely a type of crop or fertilizer, but not a list of items with percentages)

rivi  2
Input text: Koulutila. TT 80%, NN 20%. Lannoitus 14.5. YaraMila Y3 400 kg/ha. Maalaji HHt pH 6,2. 3v. nurmi
Extracted Data: Based on the provided text, here are the extracted information:

Maalaji: HHt

Multavuus: Not explicitly mentioned, but based on the maalaji (HHt), it can be inferred that the multavuus is likely "m" (multava)

pH: 6.2

Nurmen ikä: 3v (nurmesta vuotta, which means 3 years old)

Mitä viljellään?: Not explicitly mentioned, but based on the context and the fact that it's a "koulutila" (agricultural field), it can be inferred that the field is likely being used to grow grass or other crops.

rivi  3
Input text: 2 v. nurmi. HiueS. Ei lietetttä keväällä. Salpietari määrä?  Carbo 3 niiton seos TT Rubinia 35%+ Uula 15%,  RuoN Karolina 20%, NN Valtteri/Evertti 15% + apiloita
Extracted Data: Based on the provided text, I can extract the following information:

Maalaji: HeS (hiuesavi)

Multavuus: Mm (multamaa)

pH: Not mentioned in the text.

Nurmen ikä: 2 v. (2 vuotta, meaning 2 years old)

Mitä viljellään: Carbo 3 niiton seos TT Rubinia 35% + Uula 15%, RuoN Karolina 20%, NN Valtteri/Evertti 15% + apiloita (meaning a mix of different plant species with percentages indicating their proportion in the field)

rivi  4
Input text: TT Nuutti 60 %, NN Kasper 17 %, engl.rh. Riikka 10 %, Koiranheinä 3 %, PA Betty ja AA Frida yht. 10 %. Lannoitus 8.5. Yara Y3 430 kg/ha. Maalaji Ct. 2v. nurmi
Extracted Data: Here are the extracted information:

Maalaji: Ct. 2v. nurmi

Multavuus: Mm (multamaa)

pH: Not mentioned in the text.

Nurmen ikä: Not mentioned in the text.

Mitä viljellään:
TT Nuutti 60 %, NN Kasper 17 %, engl.rh. Riikka 10 %, Koiranheinä 3 %, PA Betty ja AA Frida yht. 10 %

rivi  5
Input text: TT Nuutti 60 %, NN Kasper 17 %, engl.rh. Riikka 10 %, Koiranheinä 3 %, PA Betty ja AA Frida yht. 10 %. Lannoitus 8.5. Yara Y4 470 kg/ha. Maalaji rmHtMr. 1v. nurmi
Extracted Data: Based on the provided text, here are the extracted information:

Maalaji: rmHtMr

Multavuus: Not explicitly mentioned, but based on the maalaji code "rmHtMr", it can be inferred that multavuus is likely to be "runsasmultainen" (rm) or possibly even "erittäin runsasmultainen" (erm)

pH: Not mentioned

Nurmen ikä: 1v. (one-year-old turf)

Mitä viljellään?: It seems that nothing is being grown in this field, as the text only mentions a fertilizer application and does not list any cultivated items with percentages.

Let me know if you'd like me to clarify anything!

