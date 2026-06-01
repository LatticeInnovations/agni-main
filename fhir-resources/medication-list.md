# MedicationList
Each object in the MedicationList maps to a specific formulation that can be dispensed by the Pharmacy.

## Medication List Heading : 
- Every response object has an array named `ingredient`
- Ingredient array may or may not have multiple objects in it.
- Concatenate display name of every ingredient using `+` if there are multiple ingredient. In the example below, the heading will be: `amlodipine + lisinopril`

    ```json Multiple ingredients
      "ingredient": [
          {
            "itemCodeableConcept": {
              "coding": [
                {
                  "system": "http://snomed.info/sct",
                  "code": "386864001",
                  "display": "amlodipine"
                }
              ]
            },
            "strength": {
              "numerator": {
                "value": 5,
                "system": "http://unitsofmeasure.org",
                "code": "mg"
              },
              "denominator": {
                "value": 1,
                "system": "http://unitsofmeasure.org",
                "code": "tablet"
              }
            }
          },
          {
            "itemCodeableConcept": {
              "coding": [
                {
                  "system": "http://snomed.info/sct",
                  "code": "386873009",
                  "display": "lisinopril"
                }
              ]
            },
            "strength": {
              "numerator": {
                "value": 5,
                "system": "http://unitsofmeasure.org",
                "code": "mg"
              },
              "denominator": {
                "value": 1,
                "system": "http://unitsofmeasure.org",
                "code": "tablet"
              }
            }
          }
        ]
    ``` 

## Resource Example
```json 
{
        "resourceType": "Medication",
        "id": "21223",
        "meta": {
          "versionId": "1",
          "lastUpdated": "2023-05-31T07:55:12.786+00:00",
          "source": "#pnRM0ML8aZsTsef8"
        },
        "text": {
          "status": "generated",
          "div": "<div xmlns=\"http://www.w3.org/1999/xhtml\"><div class=\"hapiHeaderText\">Amlodipine maleate 5 mg tablet</div></div>"
        },
        "code": {
          "coding": [
            {
              "system": "http://snomed.info/sct",
              "code": "1193665001",
              "display": "Amlodipine maleate 5 mg tablet"
            }
          ],
          "text": "Amlodipine maleate 5 mg tablet"
        },
        "form": {
          "coding": [
            {
              "system": "http://snomed.info/sct",
              "code": "421026006",
              "display": "Tablet"
            }
          ],
          "text": "Tablet"
        },
        "ingredient": [
          {
            "itemCodeableConcept": {
              "coding": [
                {
                  "system": "http://snomed.info/sct",
                  "code": "386864001",
                  "display": "amlodipine"
                }
              ]
            },
            "strength": {
              "numerator": {
                "value": 5,
                "system": "http://unitsofmeasure.org",
                "code": "mg"
              },
              "denominator": {
                "value": 1,
                "system": "http://unitsofmeasure.org",
                "code": "tablet"
              }
            }
          }
        ]
      }
```
