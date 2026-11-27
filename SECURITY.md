# Saugumas / Security

## Palaikomos versijos

Saugumo pataisymai leidžiami tik **naujausiai** programos versijai. Ekraniukai ją gauna per Wi-Fi
(**Nustatymai → Programinė įranga**). Senesnėms versijoms atskirų pataisymų nebus, todėl jas reikia atnaujinti.

Saugumo atnaujinimai bus leidžiami bent iki **2031-12-31**.

## Kaip pranešti apie saugumo spragą

Spragų nerašykite viešuose „Issues“. Praneškite privačiai per GitHub:
**Security → Report a vulnerability** šiame repo (<https://github.com/G32X/LT-oru-stotele/security/advisories/new>).

Nurodykite programos versiją (**Nustatymai → Informacija**), kaip spragą atkartoti ir kokį poveikį ji gali turėti.

- Gavimą patvirtinsime per **5 darbo dienas**.
- Pirminį įvertinimą pateiksime per **10 darbo dienų**.
- Pataisymą išleisime kuo greičiau, atsižvelgdami į spragos rimtumą. Kai pataisymas bus išleistas, spraga bus
  aprašyta šio repo „Security advisories“ skiltyje.

Apie aktyviai išnaudojamas spragas ir rimtus incidentus pranešama ENISA vieno langelio platformoje, kaip
reikalauja Kibernetinio atsparumo aktas (ES) 2024/2847.

## Saugumo priemonės

- Atnaujinimai pasirašomi ECDSA P-256 parašu. Ekraniukas įdiegia tik tinkamai pasirašytą programą, o į
  senesnę versiją grįžti neleidžia (nuo v1.3.13).
- Visi ryšiai vyksta per HTTPS, o serverių sertifikatai tikrinami pagal Mozilla šakninių sertifikatų sąrašą.
- Ekraniukas neatidaro jokių tinklo prievadų: jame nėra interneto serverio, nuotolinio prisijungimo ar
  debesijos paskyrų. Bluetooth išjungtas.
- Vienintelė priimanti sąsaja yra lauko jutiklio ESP-NOW paketai. Priimami tik tikslaus dydžio ir formato
  paketai ir tik iš susieto jutiklio (pirmas išgirstas jutiklis susiejamas, jį galima atsieti). Paketai
  turi tik temperatūrą, drėgmę ir baterijos įtampą, jokių komandų.
- Wi-Fi slaptažodis laikomas tik pačiame ekraniuke. Mygtukas **Nustatymai → Gamykliniai nustatymai** jį ištrina.
- Komponentų sąrašas (SBOM, CycloneDX): [`sbom.cdx.json`](sbom.cdx.json).

## Žinomi apribojimai

- Ekraniuko atmintis nešifruota. Kas turi fizinę prieigą prie ekraniuko ir USB laidą, gali nuskaityti
  išsaugotą Wi-Fi slaptažodį arba įrašyti kitą programą. Prieš atiduodami ekraniuką kitam asmeniui, atkurkite
  gamyklinius nustatymus.
- Lauko jutiklio ESP-NOW paketai nešifruojami. Netoliese esantis įrenginys teoriškai galėtų apsimesti
  susietu jutikliu ir siųsti netikrus temperatūros ar drėgmės rodmenis. Kitokio poveikio ekraniukui tai neturi.
- Orų ir radaro duomenis teikia išorinės paslaugos (LHMT, RainViewer). Jų saugumas nepriklauso šiam projektui.

---

**English summary:** security fixes are provided for the latest firmware version only, at least until
**2031-12-31**. Report vulnerabilities privately via GitHub (**Security → Report a vulnerability**);
please do not open public issues. Acknowledgement within 5 working days. Updates are ECDSA-signed with
anti-rollback, all traffic is HTTPS with certificate validation, and the device exposes no network services;
it only receives fixed-format, unencrypted ESP-NOW readings from its paired outdoor sensor.
