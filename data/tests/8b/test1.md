## Ensimmäinen testi
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

        Some of the values we are looking for can be missing or have typos in them.
        """
---

### Ensimmäinen datasetti

Kesto n.7min

rivi  1
Input text:  3 v. nurmi. 70 kg  N/ha. Ei lietettä eikä täydennyskylvetty.  Valio Carbo nurmiseos.

Extracted Data:  Based on the provided text, here is the extracted information:

Maalaji: Valio Carbo nurmiseos (AS aitosavi)

Multavuus: Mm multamaa

pH: Not mentioned

Nurmen ikä: 3 v. nurmi (years old)

Mitä viljellään: Valio Carbo nurmiseos (no further information provided)

Lannoite: None mentioned

Lannoitemäärä: None mentioned

rivi  2
Input text:  Koulutila. TT 80%, NN 20%. Lannoitus 14.5. YaraMila Y3 400 kg/ha. Maalaji HHt pH 6,2. 3v. nurmi

Extracted Data:  Based on the provided text, here is the extracted information:

Maalaji: HHt Hieno hieta
Multavuus: None (no multavuus value specified)
pH: 6.2
Nurmen ikä: 3v nurmi
Mitä viljellään: None (no specific information about what is grown)
Lannoite: YaraMila Y3
Lannoitemäärä: 400 kg/ha

Note that the multavuus value is not specified in the text, so it remains unknown. Additionally, there is no specific information provided about what is being grown (Mitä viljellään), so it cannot be extracted.

rivi  3
Input text:  2 v. nurmi. HiueS. Ei lietetttä keväällä. Salpietari määrä?  Carbo 3 niiton seos TT Rubinia 35%+ Uula 15%,  RuoN Karolina 20%, NN Valtteri/Evertti 15% + apiloita

Extracted Data:  Here's the output in the format you specified:

Maalaji: HeS Hiuesavi

Multavuus: None (there is no multavuus value provided)

pH: None (there is no pH value provided)

Nurmen ikä: 2v

Mitä viljellään: None (there is no viljellään information provided)

Lannoite: Carbo

Lannoitemäärä: None (the text does not specify a lannoitemäärä)

rivi  4
Input text:  TT Nuutti 60 %, NN Kasper 17 %, engl.rh. Riikka 10 %, Koiranheinä 3 %, PA Betty ja AA Frida yht. 10 %. Lannoitus 8.5. Yara Y3 430 kg/ha. Maalaji Ct. 2v. nurmi

Extracted Data:  Here is the extracted information:

Maalaji: Ct. 2v. nurmi
Multavuus: Mm
pH: Not mentioned (no pH value found)
Nurmen ikä: 2v
Mitä viljellään: Not specified (no specific crop or cultivar mentioned)
Lannoite: Yara Y3
Lannoitemäärä: 430 kg/ha

rivi  5
Input text:  TT Nuutti 60 %, NN Kasper 17 %, engl.rh. Riikka 10 %, Koiranheinä 3 %, PA Betty ja AA Frida yht. 10 %. Lannoitus 8.5. Yara Y4 470 kg/ha. Maalaji rmHtMr. 1v. nurmi

Extracted Data:  Here's the extracted information:

Maalaji: rmHtMr
Multavuus: rm (Runsasmultainen)
pH: Not available (no pH value mentioned)
Nurmen ikä: 1v. nurmi
Mitä viljellään: Not available (no cultivation data mentioned)
Lannoite: Yara Y4
Lannoitemäärä: 470 kg/ha

Note that the values for Mitä viljellään and Nurmen ikä were not extractable from the provided text, as they do not contain any relevant information.

---

### Toinen datasetti

Kesto: 8min

rivi  1
Input text:  2 v nurmi. HeS. Lajikkeet: Grindstad 10 kg, Rhonia 12 kg, Klaara 8 kg, Riikka 3 kg, Karoliina 3 kg/ha. Lietettä 5.5. 10 t/ha, 20.4. Se-salpietari 350 kg/ha.

Extracted Data:  Based on the provided text, here is the extracted information:

Maalaji: HeS hiuesavi

Multavuus: vm vähämultainen (since it's close to maalaji written together with it)

pH: Not mentioned or not relevant for this specific text

Nurmen ikä: 2v nurmi

Mitä viljellään: No explicit information provided, but the text only lists different seed types without quantities.

Lannoite: No information provided about the fertilizer type.

Lannoitemäärä: No quantity mentioned.

rivi  2
Input text:  Grindstad-timotei, Minto-nurminata

Extracted Data:  Based on the provided text "Grindstad-timotei, Minto-nurminata", I extracted the following information:

Maalaji: HtMr Hietamoreeni
Multavuus: vm (vähämultainen)
pH: Not mentioned in the text
Nurmen ikä: Not mentioned in the text
Mitä viljellään: Not mentioned in the text
Lannoite: Not mentioned in the text
Lannoitemäärä: Not mentioned in the text

Note that some values might be missing or have typos, as per your guidance.

rivi  3
Input text:  Timotei Tryggve, nurminata SW Minto

Extracted Data:  Based on the provided text "Timotei Tryggve, nurminata SW Minto", I extracted the following information:

Maalaji: 

Multavuus: 

pH: 

Nurmen ikä: 2v

Mitä viljellään: 

Lannoite: 

Lannoitemäärä:

rivi  4
Input text:  LUOMU.

Extracted Data:  After analyzing the text "LUOMU" in Finnish, I extracted the following information:

Maalaji: (no maalaji specified)

Multavuus: (no multavuus specified)

pH: (no pH value specified)

Nurmen ikä: (no nurmen ikä specified)

Mitä viljellään: (no specific cultivation information provided)

Lannoite: (no fertilizer type specified)

Lannoitemäärä: (no fertilizer amount specified)

Please note that the text "LUOMU" does not provide any specific values for these parameters, as it only consists of a single word. If you'd like me to help with anything else or provide more information based on the provided lists and examples, feel free to ask!

rivi  5
Input text:  Vihti Kotkaniemi, Yaran D-arvoseuranta

Extracted Data:  Based on the provided text, here is the extracted information:

Maalaji: BCt ruskosammalsaraturve
Multavuus: m multava
pH: [extracted pH] (no value found)
Nurmen ikä: [extracted nurmen ikä] (no value found)
Mitä viljellään: [extracted mitä viljellään] (no value found)
Lannoite: Yaran D-arvoseuranta
Lannoitemäärä: [extracted lannoitemäärä] (no value found)

Note that some of the values were not extractable due to missing or typos in the text.

