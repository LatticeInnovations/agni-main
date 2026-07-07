# DocumentReference: Immunization
- This consist of Document reference that contains the url of photo uploaded by user in vaccination which links to vaccination encounter.

## Resource Example

```json
{
  "resourceType": "DocumentReference",
  "status": "current",
  "description": "Vaccination certificate",
  "subject" : "Patient/patient-id",
  "content": [
    {
      "attachment": {
        "url": "https://localhost:3000/uploads/1717669846001.jpg",
        "title": "1717669846001.jpg"
      }
    }
  ],
  "context" : {
    "encounter" {
        "reference" : "Encounter/<vaccination-sub-encounter-id>"
    }
  }
}
