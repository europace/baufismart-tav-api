 
# Top Angebot Vertrieb (TAV)
 
Top Angebot Vertrieb (TAV) – ist ein Service zur Ermittlung der Top-Baufinanzierungskondition für EUROPACE Partner
Die Schnittstelle liefert zu mehreren Zinsbindungen die jeweils beste Baufinanzierungskondition des anfragenden Partners auf Basis seiner Handelsbeziehungen in Europace.

## Anwendungsbeispiele
 
* Konditionstableau auf der Website eines Europace Partners oder
* Online Baufinanzierungsrechner ("Was kann ich mir leisten" Rechner)
 
## Fachliche Eckdaten
 
TAV berücksichtigt bei der Ermittlung der besten Baufinanzierungskondition die Produktarten Annuitätendarlehen und Forward Darlehen.
Bei Angabe eines Auszahlungsdatums, dass > 6 Monate in der Zukunft liegt, werden neben Annuitätendarlehen auch Forward Darlehen berücksichtigt.

## Inhalt
* [Datenformat der Schnittstelle](#datenformat-der-tav-schnittstelle)

## HTTP-Rest Service
Der Service ist über einen Rest Service mit folgenden Pfad aufrufbar
```
https://xxx/tav/standard/ermittleKonditionen
```

## Security
Die Schnittstelle ist über HTTPS ansprechbar. Weitere Sicherheitsdetails sind Bestandteil des jeweiligen Anbindungsprojekts.

## Datenformat der TAV Schnittstelle

Die TAV Standard API stellt die Konditionen als JSON Dokument bereit.

### Beispiel einer Anfrage
```
{
  "zinsBindungInJahren": [
    5, 10, 15, 20
  ],
  "darlehensSumme": 100000,
  "tilgungsSatz": 1,
  "tilgungsArt": "LAUFEND",
  "finanzierungsZweck": "KAUF",
  "immobilie": {
    "eigengenutzt": true,
    "fremdgenutzt": false,
    "kaufPreis": 150000,
    "objektArt": "WOHNUNG",
    "postleitzahl": "10247"
  },
  "kunde": {
    "anstellungsVerhaeltnis": "ANGESTELLTER"
  },
  "vermittler": "TESTPARTNER",
  "auszahlungsTermin": "2015-10-01"
}
```
 

### Beispiel einer Antwort
```
{
  "konditionen": [
    {
      "zinsBindungInJahren": 5,
      "laufzeitInMonaten": 858,
      "sollZins": 0.9,
      "effektivZins": 0.9,
      "monatlicheRate": 158.33,
      "restschuld": 94887.95,
      "produktAnbieter": "BW_BANK",
      "produktArt": "ANNUITAET",
      "summeZahlungen": 135629.44,
      "grundbuchKosten": 273
    },
    {
      "zinsBindungInJahren": 10,
      "laufzeitInMonaten": 742,
      "sollZins": 1.46,
      "effektivZins": 1.47,
      "monatlicheRate": 205,
      "restschuld": 89240.15,
      "produktAnbieter": "PSD_BERLIN",
      "produktArt": "ANNUITAET",
      "summeZahlungen": 151884.95,
      "grundbuchKosten": 273
    },
    {
      "zinsBindungInJahren": 15,
      "laufzeitInMonaten": 659,
      "sollZins": 2.02,
      "effektivZins": 2.04,
      "monatlicheRate": 251.67,
      "restschuld": 82495.84,
      "produktAnbieter": "PSD_BERLIN",
      "produktArt": "ANNUITAET",
      "summeZahlungen": 165547.16,
      "grundbuchKosten": 273
    },
    {
      "zinsBindungInJahren": 20,
      "laufzeitInMonaten": 613,
      "sollZins": 2.41,
      "effektivZins": 2.44,
      "monatlicheRate": 284.17,
      "restschuld": 74333.9,
      "produktAnbieter": "DKB",
      "produktArt": "ANNUITAET",
      "summeZahlungen": 173945.08,
      "grundbuchKosten": 273
    }
  ]
}
```

