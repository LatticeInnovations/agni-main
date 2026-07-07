---
order: 800
---

## Encounter
> This is Encounter resource


## Resource example 

```
{
        "resourceType": "Encounter",
        "id": "24483",
        "meta": {
          "versionId": "1",
          "lastUpdated": "2023-08-22T06:06:10.326+00:00",
          "source": "#xxlHFBHOhJ5zUq5u"
        },
        "identifier": [
          {
            "system": "http://hl7.org/fhir/sid/sn",
            "value": "f53da004-10f9-4caa-99cd-7c826b029383"
          }
        ],
        "status": "planned",
        "subject": {
          "reference": "Patient/24476"
        },
        "appointment": [
          {
            "reference": "Appointment/24482"
          }
        ]
      }
```
