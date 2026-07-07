## Overview
- This consist of medication Request / Prescription.

## Resource Example : 

```
{
        "resourceType": "MedicationRequest",
        "id": "32476",
        "meta": {
          "versionId": "1",
          "lastUpdated": "2024-02-28T05:19:30.948+00:00",
          "source": "#NV7eHk8ilQiL9aBA"
        },
        "identifier": [
          {
            "system": "http://hl7.org/fhir/sid/sn",
            "value": "11a0efc8-7431-43a7-9184-e741a12d6f70"
          }
        ],
        "intent": "order",
        "medicationReference": {
          "reference": "Medication/21226" // reference to medication list resource
        },
        "subject": {
          "reference": "Patient/32323" // reference to Patient resource
        },
        "encounter": {
          "reference": "Encounter/32355" // reference to Encounter resource
        },
        "groupIdentifier": {
          "system": "http://hospital.smarthealthit.org/prescriptions",
          "value": "00032323"
        },
        "dosageInstruction": [
          {
            "timing": {
              "repeat": {
                "boundsDuration": {
                  "unit": "days",
                  "system": "http://unitsofmeasure.org",
                  "code": "d"
                },
                "frequency": 1,
                "period": 5,
                "periodUnit": "d"
              }
            },
            "doseAndRate": [
              {
                "doseQuantity": {
                  "value": 2,
                  "unit": "Tablet",
                  "code": "421026006"
                }
              }
            ]
          }
        ]
      }
```
