## Description
This is a record keeping encnounter of vitals created at the given time

```json
{
        "resourceType": "Encounter",
        "identifier": [
          {
            "system": "http://hl7.org/fhir/sid/sn",
            "value": "9a150ba5-db20-4b2b-a81a-e90d4bc06884" // uuid
          }
        ],
        "status": "finished",   //  the status can be changed to 
        "type": [
          {
            "coding": [
              {
                "system": "http://www.thelattice.org/encounter-type",
                "code": "vital-encounter",
                "display": "Vital management"
              }
            ]
          }
        ],
        "subject": {
          "reference": "Patient/254"
        },
        "period": {
          "start": "2024-09-30T17:35:00+05:30",
          "end": "2024-09-30T17:35:00+05:30"
        },
        "partOf": {
          "reference": "Encounter/269"  // links to appointment encounter
        },

      }
```
