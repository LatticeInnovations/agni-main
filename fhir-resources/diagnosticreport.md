# DiagnosticReport 
DiagnosticReport resource is used to record symptoms and diagnoses made during the patient.

## Resource Details
> - We can refer to the [link](https://hl7.org/fhir/R4/diagnosticreport.html) as well to check as per FHIR standard.

## Resource Example 
```
{
  "resourceType": "DiagnosticReport",
  "code": {
    "coding": [
      {
        "system": "http://loinc.org",
        "code": "11502-2",
        "display": "Laboratory report"
      }
    ]
  },
  "subject": {
    "reference": "Patient/{patient id}"
  },
  "encounter": {
    "reference": "Encounter/{encounter id}"
  },
  "issued": "2024-09-18T12:00:00Z",
  "extension": [
    {
      "url": "http://hl7.org/fhir/StructureDefinition/DocumentReference",
      "valueReference": {
        "reference": "DocumentReference/789"
      }
    }
  ]
}

```
