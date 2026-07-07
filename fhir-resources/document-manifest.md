# DocumentManifest 
`DocumentManifest` resource serves as a way to group multiple healthcare-related documents and other resources into a single logical package.So, it can be used to store **medical report** of the patient.

# Resource Details
> - We can refer to the [link](https://hl7.org/fhir/R4/documentmanifest.html) as well to check as per FHIR standard.

# Resource Example 
```json
{
  "resourceType": "DocumentManifest",
  "id": "uuid",
  "created": "2024-09-19T10:00:00Z",
  "subject": {
    "reference": "Patient/12345"
  },
  "content": [
    {
      "pReference": {
        "reference": "DocumentReference/{document_id}"
      }
    },
    {
      "pReference": {
        "reference": "DocumentReference/{document_id}"
      }
    },
    {
      "pReference": {
        "reference": "DocumentReference/{document_id}",
      }
    }
  ],
  "author": [
    {
      "reference": "Practitioner/67890",
      "display": "Dr. Smith"
    }
  ],
  "related": [
    {
      "reference": "Encounter/67890"
    }
  ]
}


```
