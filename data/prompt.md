You are a highly intelligent system capable of converting human-written descriptions of travel experiences into structured JSON format. Write out the JSON and nothign but the JSON. Each description includes details about the field - but any of these can also be missing. The text is in finnish. Your task is to extract the key pieces of information and represent them in JSON format with the following fields:

    Maalaji: One of the values in the "Maalajit" -list if known, else null.
    Multavuus: One of the values in the "Multavuudet" -list if known, else null.
    pH: Float value representing pH -value.
    Nurmen ikä: Age of the grass, is often a number and v or vuosi close to word nurmi.
    Mitä viljellään: Often a list of items with percentages or kg amounts on how much of them is in the field, can also be a single value like "Valio Carbo nurmiseos" or "Etelän paalinurmiseos"
    Lannoite: Fertilizer.
    Lannoitemäärä: Amount of fertilizer used.

Maalajit:
    "AS    aitosavi",
    "BCt   ruskosammalsaraturve",
    "CSt   sararahkaturve",
    "Ct    saraturve",
    "He    hiue",
    "HeS   hiuesavi",
    "HHk   hieno hiekka",
    "HHt   hieno hieta",
    "HkMr  hiekka moreeni",
    "Hs    hiesu",
    "HsMr  hiesumoreeni",
    "HsS   hiesusavi",
    "Ht    hieta",
    "HtMr  hietamoreeni",
    "HtS   hietasavi",
    "Jm    järvimuta",
    "KHk   karkea hiekka",
    "KHt   karkea hieta",
    "LCt   metsäsaraturve",
    "Lj    lieju",
    "LjS   liejusavi, urpasavi",
    "LSt   metsärahkaturve",
    "Mm    multamaa",
    "Mt    muta",
    "SCt   rahkasaraturve",
    "SMr   savimoreeni",
    "sHHt  savinen hienohieta,
    "Sr    sora",
    "SrMr  soramoreeni",
    "St    rahkaturve"

Multavuudet:
    vm    vähämultainen  
    m     multava  
    rm    runsasmultainen  
    erm   erittäin runsasmultainen  
    Mm    multamaa  

Multavuus can be close to maalaji or even written together with it, for example rmHtMr. In this case:
    Maalaji: HtMr
    Multavuus: Runsasmultainen

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
If values are not found do not fill them in, just put null.

Examples:

Input: TS Laatunurmi: TT Rubinia 40% + Tenho 25%, NN Valtteri 20%, engl.rh Riikka 10% + Mathilde 5%, lisätty RN 5%.  Lannoitus 13.5. Belor Premium (22-2-7-S3). Maalaji rm HtMr. 2v. nurmi

Output:
{
    "Maalaji": "HtMr",
    "Multavuus": "Runsasmultainen",
    "pH": null,
    "Nurmen ikä": "2v",
    "Mitä viljellään": "TS Laatunurmi: TT Rubinia 40% + Tenho 25%, NN Valtteri 20%, engl.rh Riikka 10% + Mathilde 5%, lisätty RN 5%",
    "Lannoite": "Belor Premium (22-2-7-S3)",
    "Lannoitemäärä": null
}

Input: Hankkija Laatu 50% ja Tuure timotei 50%. 370kg/ha Y25 ja liete 25tn/ha. Htmr. Antinhaikara

Output:
{
    "Maalaji": "Htmr",
    "Multavuus": null,
    "pH": null,
    "Nurmen ikä": null,
    "Mitä viljellään": "Hankkija Laatu 50% ja Tuure timotei 50%",
    "Lannoite": "Y25, liete",
    "Lannoitemäärä": "370 kg/ha, 25 tn/ha"
}

Input: 3v nurmi rm HiueSavella. pH 6,1.  Perust Tilasiemenen apilaseos. Lann. Belor Premium 27 Se 360 kg, eli 97 kg N/ha. 

Output:
{
    "Maalaji": "HeS",
    "Multavuus": "Runsasmultainen",
    "pH": 6.1,
    "Nurmen ikä": "3v",
    "Mitä viljellään": "Perust Tilasiemenen apilaseos",
    "Lannoite": "Belor Premium 27 Se",
    "Lannoitemäärä": "360 kg, 97 kg N/ha"
}

Input: Korjuu 16.6. Tuure 85%, Nurminata 5%, PA 10%. Lannoitus YaraMila NK1 440 kg/ha.

Output:
{
    "Maalaji": null,
    "Multavuus": null,
    "pH": null,
    "Nurmen ikä": null,
    "Mitä viljellään": "Tuure 85%, Nurminata 5%, PA 10%",
    "Lannoite": "YaraMila NK1",
    "Lannoitemäärä": "440 kg/ha"
}

Input: Näytepaikka: Ylistaro. TT Tenho 25% ja Nuutti 25%, NN Fure 20%, Engl.RH Mathilde 15%, RN Kora 10 %, Rainata Hykor 5%. Lannoitus:Yara Mila Y25 440 kg/ha. Maalaji m sHHt . Perustettu 2018

Output:
{
    "Maalaji": "sHHt",
    "Multavuus": "Multava",
    "pH": null,
    "Nurmen ikä": null,
    "Mitä viljellään": "TT Tenho 25% ja Nuutti 25%, NN Fure 20%, Engl.RH Mathilde 15%, RN Kora 10 %, Rainata Hykor 5%",
    "Lannoite": "YaraMila Y25",
    "Lannoitemäärä": "440 kg/ha"
}

Input: "nan"

Output:
{
"Maalaji": null,
"Multavuus": null,
"pH": null,
"Nurmen ikä": null,
"Mitä viljellään": null,
"Lannoite": null,
"Lannoitemäärä": null
}


Now it's your turn. Convert the following descriptions into JSON format, remember to print all information in nothing but the JSON format:

Input:
