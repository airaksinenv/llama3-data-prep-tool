## Toinen testi
        prompt = f"""
        Extract the following information from the text below, the text is in finnish:
        - Maalaji
        - Multavuus
        - pH
        - Nurmen ikä
        - Mitä viljellään
        - Lannoite
        - Lannoitemäärä

        Text: "{text}"

        Provide the output in this format:
        Maalaji: [extracted maalaji]
        Multavuus: [extracted multavuus]
        ph: [extracted pH]
        Nurmen ikä: [extracted nurmen ikä]
        Mitä viljellään: [extracted mitä viljellään]
        Lannoite: [extracted lannoite]
        Lannoitemäärä: [extracted lannoitemäärä]

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

        Lannoitus and lannoitusmäärä:
            for example from input: Lannoitus 14.5. YaraMila Y3 400 kg/ha.
            14.5 is the date (not to be extracted)
            Lannoitus: YaraMila Y3
            Lannoitusmäärä: 400 kg/ha

            Another example:  20.4. Se-salpietari 350 kg/ha.
            20.4. is the date (not to be extracted)
            Lannoitus: Se-salpietari
            Lannoitusmäärä: 350 kg/ha

        Some of the values we are looking for can be missing or have typos in them.
        If values are not found do not fill them in, just put None.
        No extra information is required from you, just the output in the requested format.
        """
---

### Ensimmäinen datasetti

Kesto 7m 41.3s

rivi  1
Input text:  3 v. nurmi. 70 kg  N/ha. Ei lietettä eikä täydennyskylvetty.  Valio Carbo nurmiseos.

Extracted Data:  Here is the extracted information:

Maalaji: Valio Carbo
Multavuus: None
pH: None
Nurmen ikä: 3 v.
Mitä viljellään: Valio Carbo nurmiseos
Lannoite: None
Lannoitemäärä: None

rivi  2
Input text:  Koulutila. TT 80%, NN 20%. Lannoitus 14.5. YaraMila Y3 400 kg/ha. Maalaji HHt pH 6,2. 3v. nurmi

Extracted Data:  Here is the extracted information:

Maalaji: HHt
Multavuus: vm
pH: 6.2
Nurmen ikä: 3v
Mitä viljellään: None (no specific information provided)
Lannoite: YaraMila Y3
Lannoitemäärä: 400 kg/ha

rivi  3
Input text:  2 v. nurmi. HiueS. Ei lietetttä keväällä. Salpietari määrä?  Carbo 3 niiton seos TT Rubinia 35%+ Uula 15%,  RuoN Karolina 20%, NN Valtteri/Evertti 15% + apiloita

Extracted Data:  Here is the extracted information:

Maalaji: He   hiue

Multavuus: None

pH: None

Nurmen ikä: 2v

Mitä viljellään: Carbo 3 niiton seos TT Rubinia 35%+ Uula 15%, RuoN Karolina 20%, NN Valtteri/Evertti 15%

Lannoite: Salpietari

Lannoitemäärä: None

rivi  4
Input text:  TT Nuutti 60 %, NN Kasper 17 %, engl.rh. Riikka 10 %, Koiranheinä 3 %, PA Betty ja AA Frida yht. 10 %. Lannoitus 8.5. Yara Y3 430 kg/ha. Maalaji Ct. 2v. nurmi

Extracted Data:  Based on the provided text, here is the extracted information:

Maalaji: Ct 2v nurmi
Multavuus: Mm
pH: None
Nurmen ikä: 2v
Mitä viljellään: None
Lannoite: Yara Y3
Lannoitemäärä: 430 kg/ha

rivi  5
Input text:  TT Nuutti 60 %, NN Kasper 17 %, engl.rh. Riikka 10 %, Koiranheinä 3 %, PA Betty ja AA Frida yht. 10 %. Lannoitus 8.5. Yara Y4 470 kg/ha. Maalaji rmHtMr. 1v. nurmi

Extracted Data:  Here's the extracted information:

Maalaji: rmHtMr
Multavuus: rm
pH: None
Nurmen ikä: 1v
Mitä viljellään: Nuutti 60 %, Kasper 17 %, Riikka 10 %, Koiranheinä 3 %, Betty ja Frida yht. 10 %
Lannoite: Yara Y4
Lannoitemäärä: 470 kg/ha

---

### Toinen datasetti

Kesto 8m 5.1s

rivi  1
Input text:  2 v nurmi. HeS. Lajikkeet: Grindstad 10 kg, Rhonia 12 kg, Klaara 8 kg, Riikka 3 kg, Karoliina 3 kg/ha. Lietettä 5.5. 10 t/ha, 20.4. Se-salpietari 350 kg/ha.

Extracted Data:  Here is the extracted information:

Maalaji: HeS hiuesavi
Multavuus: None
pH: None
Nurmen ikä: 2v
Mitä viljellään: None
Lannoite: Se-salpietari
Lannoitemäärä: 350 kg/ha

rivi  2
Input text:  Grindstad-timotei, Minto-nurminata

Extracted Data:  Based on the provided text "Grindstad-timotei, Minto-nurminata", I extracted the following information:

Maalaji: Minto-nurminata
Multavuus: None
pH: None
Nurmen ikä: None
Mitä viljellään: None
Lannoite: None
Lannoitemäärä: None

Please note that since there is no specific information provided about maalaji, multavuus, pH, nurmen ikä, mitä viljellään, lannoite, and lannoitemäärä, I left them as None.

rivi  3
Input text:  Timotei Tryggve, nurminata SW Minto

Extracted Data:  Based on the text "Timotei Tryggve, nurminata SW Minto", I extracted the following information:

Maalaji: AS (aitosavi)
Multavuus: None
pH: None
Nurmen ikä: None
Mitä viljellään: None
Lannoite: None
Lannoitemäärä: None

Please note that the values for multavuus, pH, nurmen ikä, mitä viljellään, lannoite, and lannoitemäärä were not found in the provided text.

rivi  4
Input text:  LUOMU.

Extracted Data:  Based on the provided text, I extracted the following information:

Maalaji: None
Multavuus: None
pH: None
Nurmen ikä: None
Mitä viljellään: None
Lannoite: None
Lannoitemäärä: None

Since the original text only contains the word "LUOMU" and does not provide any specific information about maalaji, multavuus, pH, nurmen ikä, or lannoitus/lannoitemäärä.

rivi  5
Input text:  Vihti Kotkaniemi, Yaran D-arvoseuranta

Extracted Data:  Here is the extracted information:

Maalaji: AS aitosavi
Multavuus: vm vähämultainen
pH: None
Nurmen ikä: 2v
Mitä viljellään: None
Lannoite: Yaran D-arvoseuranta
Lannoitemäärä: None

