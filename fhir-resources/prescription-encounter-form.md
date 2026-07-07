## Description : 
- When user will fill up the prescription, a new sub encounter will be created with type `prescription-encounter-form`. This encounter will have reference to the main appointment encounter.

```json
{
        "resourceType": "Encounter",
        "id": "3605",
        "meta": {
          "versionId": "1",
          "lastUpdated": "2024-12-02T07:25:50.462+00:00",
          "source": "#7swp2Kgl1KK9B2xT"
        },
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
                "system": "http://your-custom-coding-system",
                "code": "prescription-encounter-form",
                "display": "Prescription managemment"
              }
            ]
          }
        ],
        "subject": {
          "reference": "Patient/3595"
        },
        "period": {
          "start": "2024-12-02T01:43:00+05:30",
          "end": "2024-12-02T01:43:00+05:30"
        },
        "partOf": {
          "reference": "Encounter/3600"
        }
}
