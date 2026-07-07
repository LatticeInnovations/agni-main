# Immunization
Immunization resource captures the details of the vaccine taken by a patient.

```Json
{
  "resourceType": "Immunization",
  "status": "completed",
  "vaccineCode": {
    "coding": [
      {
        "system": "urn:oid:1.2.36.1.2001.1005.17",
        "code": "19"
      }
    ],
    "text": "Bacillus Calmette-Guerin vaccine(BCG)"
  },
  "patient": {
    "reference": "Patient/<patient-id>"
  },
  "occurrenceDateTime": "2015-01-15",
  "primarySource": true,
  "performer" : [
    {
        "actor" : {
            "reference":  "Practitioner/<practitioner-id"
        }
    }
  ],
  "manufacturer": {
    "reference" : "Organization/<org-id>"
  },
  "note": [
    {
      "text": "Notes on administration of a historical vaccine"
    }
  ],
  "encounter" : "Encounter/<vaccine-sub-encounter-id>",
  "lotNumber" : "VX-2023-00452",
  "expirationDate" : "2015-01-15"
}
```
