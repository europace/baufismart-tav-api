 
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
      "laufzeitInMonaten": 844,
      "sollZins": 0.95,
      "effektivZins": 0.95,
      "monatlicheRate": 162.5,
      "restschuld": 94794,
      "produktAnbieter": "DSL",
      "produktArt": "ANNUITAET"
    },
    {
      "zinsBindungInJahren": 10,
      "laufzeitInMonaten": 783,
      "sollZins": 1.23,
      "effektivZins": 1.24,
      "monatlicheRate": 185.83,
      "restschuld": 89270.99,
      "produktAnbieter": "MHB",
      "produktArt": "FORWARD"
    },
    {
      "zinsBindungInJahren": 15,
      "laufzeitInMonaten": 699,
      "sollZins": 1.72,
      "effektivZins": 1.73,
      "monatlicheRate": 226.67,
      "restschuld": 82792.55,
      "produktAnbieter": "WL_Bank",
      "produktArt": "ANNUITAET"
    },
    {
      "zinsBindungInJahren": 20,
      "laufzeitInMonaten": 664,
      "sollZins": 1.97,
      "effektivZins": 1.99,
      "monatlicheRate": 247.5,
      "restschuld": 75388.09,
      "produktAnbieter": "VOBA_TEST",
      "produktArt": "FORWARD"
    }
  ]
}
```

