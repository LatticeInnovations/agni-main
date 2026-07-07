## Description : 
- When a user creates a prescription by uploading a document, then a new encounter is created with type `prescription-encounter-document`. This encounter will have reference to the main appointment encounter. The new Medication Request resource created will have reference to the DocumentReference resource.

```json
{
      "resourceType": "Encounter",
      "id": "767",
      "meta": {
        "versionId": "1",
        "lastUpdated": "2024-12-02T20:54:20.935+05:30",
        "source": "#s9qHWrPstof9izKJ"
      },
      "identifier": [ {
        "system": "http://hl7.org/fhir/sid/sn/prescriptionDocument",
        "value": "1e7c0c7f-969c-43e4-b5fc-bcc075185fb6"
      } ],
      "type": [ {
        "coding": [ {
          "system": "http://your-custom-coding-system",
          "code": "prescription-encounter-document",
          "display": "Prescription document encounter"
        } ]
      } ],
      "subject": {
        "reference": "Patient/13"
      },
      "participant": [ {
        "individual": {
          "reference": "Practitioner/2"
        }
      } ],
      "period": {
        "start": "2024-10-08T17:00:00+05:30",
        "end": "2024-10-08T17:00:00+05:30"
      },
      "partOf": {
        "reference": "Encounter/75",
        "display": "Primary Encounter"
      }
}
