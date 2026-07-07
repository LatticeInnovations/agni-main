## Description : 
This is sub encounter created when a symptom and diagnosis is created. Condition resource is linked to this sub encounter and this sub encounter is linked to main appointment encounter.

```json
{
  "resourceType": "Encounter",
  "id": "355",
  "meta": {
    "versionId": "1",
    "lastUpdated": "2024-10-21T11:31:04.157+05:30",
    "source": "#fobJtOOboSoYz6hf"
  },
  "identifier": [ {
    "system": "http://hl7.org/fhir/sid/sn/diagnosis",
    "value": "9a248831-23a6-4957-8848-93ebb9809c8a"
  } ],
  "type": [ {
    "coding": [ {
      "system": "http://your-custom-coding-system",
      "code": "symptom-diagnosis-encounter",
      "display": "Symptom Diagnosis encounter"
    } ]
  } ],
  "subject": {
    "reference": "Patient/7"
  },
  "participant": [ {
    "individual": {
      "reference": "Practitioner/2"
    }
  } ],
  "period": {
    "start": "2024-10-21",
    "end": "2024-10-21"
  },
  "partOf": {
    "reference": "Encounter/75",
    "display": "Primary Encounter"
  }
}
```
