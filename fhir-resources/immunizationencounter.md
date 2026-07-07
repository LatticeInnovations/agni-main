# ImmunizationEncounter 
- When the hospital fills a patient's immunization details, a new sub encounter will be created with type `Immunization management`. This encounter will have reference to the main appointment encounter.
- This encounter acts as a bridge between Immunization and Document reference resource.

```json
{
        "resourceType": "Encounter",
        "identifier": [
          {
            "system": "http://hl7.org/fhir/sid/sn",
            "value": "33d7005a-82cd-428e-9dc7-ff624476fe62"
          }
        ],
        "type": [
          {
            "coding": [
              {
                "system": "http://snomed.info/sct",
                "code": "384810002",
                "display": "Immunization management"
              }
            ]
          }
        ],
        "subject": {
          "reference": "Patient/<patient-id>"
        },
        "period": {
          "start": "2024-12-02T01:43:00+05:30",
          "end": "2024-12-02T01:43:00+05:30"
        },
        "partOf": {
          "reference": "Encounter/<appointment-encounter-id>"
        }
}
