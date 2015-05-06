# TAV Standard API

Top Angebot Vertrieb (TAV) – ist ein Service zur Ermittlung der Top-Baufinanzierungskondition für EUROPACE Partner
Die Schnittstelle liefert zu mehreren Zinsbindungen die jeweils beste Baufinanzierungskondition des anfragenden Partners auf Basis seiner Handelsbeziehungen in Europace.
Bei Angabe eines Auszahlungsdatums werden neben Annuitätendarlehen auch Forward Darlehen bei der Bestzinsermittlung berücksichtigt. 


## Inhalt
* [Datenformat der Schnittstelle](#datenformat-der-tav-schnittstelle)

## HTTP-Rest Service
Der Service ist über einen Rest Service mit folgenden Pfad aufrufbar
```
https://xxx/tav/standard/ermittleKonditionen
```

## Datenformat der TAV Schnittstelle

Die TAV Standard API stellt die Konditionen als JSON Dokument bereit.

### Beispiel einer Anfrage
```
{
  "zinsBindungInJahren"
:
  [5, 10, 20], "darlehensSumme"
:
  250000, "tilgungsSatz"
:
  1, "tilgungsArt"
:
  "LAUFEND", "finanzierungsZweck"
:
  "KAUF", "immobilie"
:
  {
    "eigengenutzt"
  :
    true, "fremdgenutzt"
  :
    false, "kaufPreis"
  :
    300000, "objektArt"
  :
    "WOHNUNG", "postleitzahl"
  :
    "82475"
  }
,
  "kunde"
:
  {
    "anstellungsVerhaeltnis"
  :
    "ANGESTELLTER"
  }
,
  "vermittler"
:
  "vertriebsName", "auszahlungsTermin"
:
  {
    "chronology"
  :
    {
      "zone"
    :
      {
        "fixed"
      :
        true, "id"
      :
        "UTC"
      }
    }
  ,
    "centuryOfEra"
  :
    20, "yearOfEra"
  :
    2015, "yearOfCentury"
  :
    15, "weekyear"
  :
    2015, "monthOfYear"
  :
    5, "weekOfWeekyear"
  :
    19, "year"
  :
    2015, "dayOfMonth"
  :
    5, "dayOfWeek"
  :
    2, "era"
  :
    1, "dayOfYear"
  :
    125, "fields"
  :
    [{
      "lenient": false,
      "leapDurationField": {"unitMillis": 86400000, "precise": true, "name": "days", "type": {"name": "days"}, "supported": true},
      "minimumValue": -292275054,
      "maximumValue": 292278993,
      "rangeDurationField": null,
      "durationField": {
        "unitMillis": 31556952000,
        "precise": false,
        "name": "years",
        "type": {"name": "years"},
        "supported": true
      },
      "name": "year",
      "type": {"durationType": {"name": "years"}, "rangeDurationType": null, "name": "year"},
      "supported": true
    }, {
      "lenient": false,
      "leapDurationField": {"unitMillis": 86400000, "precise": true, "name": "days", "type": {"name": "days"}, "supported": true},
      "minimumValue": 1,
      "maximumValue": 12,
      "rangeDurationField": {
        "unitMillis": 31556952000,
        "precise": false,
        "name": "years",
        "type": {"name": "years"},
        "supported": true
      },
      "durationField": {
        "unitMillis": 2629746000,
        "precise": false,
        "name": "months",
        "type": {"name": "months"},
        "supported": true
      },
      "name": "monthOfYear",
      "type": {"durationType": {"name": "months"}, "rangeDurationType": {"name": "years"}, "name": "monthOfYear"},
      "supported": true
    }, {
      "minimumValue": 1,
      "maximumValue": 31,
      "rangeDurationField": {
        "unitMillis": 2629746000,
        "precise": false,
        "name": "months",
        "type": {"name": "months"},
        "supported": true
      },
      "unitMillis": 86400000,
      "lenient": false,
      "durationField": {"unitMillis": 86400000, "precise": true, "name": "days", "type": {"name": "days"}, "supported": true},
      "name": "dayOfMonth",
      "type": {"durationType": {"name": "days"}, "rangeDurationType": {"name": "months"}, "name": "dayOfMonth"},
      "supported": true,
      "leapDurationField": null
    }], "fieldTypes"
  :
    [{"durationType": {"name": "years"}, "rangeDurationType": null, "name": "year"}, {
      "durationType": {"name": "months"},
      "rangeDurationType": {"name": "years"},
      "name": "monthOfYear"
    }, {"durationType": {"name": "days"}, "rangeDurationType": {"name": "months"}, "name": "dayOfMonth"}], "values"
  :
    [2015, 5, 5]
  }
}
```
 

### Beispiel einer Antwort
```
{
  "konditionen"
:
  [{
    "zinsBindungInJahren": 5,
    "laufzeitInMonaten": 400,
    "sollZins": 3.5,
    "effektivZins": 2.7,
    "monatlicheRate": 255.66,
    "restschuld": 28001.99,
    "produktAnbieter": {"value": "DSL_BANK"},
    "produktArt": "FORWARD"
  }, {
    "zinsBindungInJahren": 3,
    "laufzeitInMonaten": 400,
    "sollZins": 3.5,
    "effektivZins": 2.7,
    "monatlicheRate": 255.66,
    "restschuld": 28001.99,
    "produktAnbieter": {"value": "DSL_BANK"},
    "produktArt": "ANNUITAET"
  }]
}
```

