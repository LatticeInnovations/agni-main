## Description : 
> This document contains information how the ICD code will be saved in Database and how to API to fetch all the ICD codes.

## Ways to store data : 
- ICD codes has only three values : `code`, `short description`, `long description`.
- We can store the data either in a `JSON file` or in a `Table in database` with above three columns.
- We are known to a fact that all the records at any given point of time will be there at client end.
- So client needs to fetch all the records at once, during 1st time sync.
- For above memtioned points, both `JSON` file or `table in Database` will work fine.
- But if in future, searching and quering is done at server end, then I would recommend it to store in database as searching will be fast at database rather than a JSON file.

### 1. Fetch the ICD 10 codes
> GET : /codes/icd

#### Response body
- Response will have all the records.
```
{
 "status" : 1,
 "message" : "data fetched",
 "data" : [
    {
      "code" : "A000",
      "shortDescription" : "Cholera due to Vibrio cholerae 01, biovar cholerae",
      "longDescription" : "Cholera due to Vibrio cholerae 01, biovar cholerae"
    }
  ]
}
```

### FHIR Resource Example : Condition Resource diagnosed for a patient

> To know more about Condition resource [click here](https://hl7.org/fhir/R4/condition.html)

```
{
  "resourceType": "Condition",
  "id": "{condition id}",
  "clinicalStatus": {
    "coding": [
      {
        "system": "http://terminology.hl7.org/CodeSystem/condition-clinical",
        "code": "active",
        "display": "Active"
      }
    ]
  },
  "verificationStatus": {
    "coding": [
      {
        "system": "http://terminology.hl7.org/CodeSystem/condition-ver-status",
        "code": "confirmed",
        "display": "Confirmed"
      }
    ]
  },
  "category": [
    {
      "coding": [
        {
          "system": "http://terminology.hl7.org/CodeSystem/condition-category",
          "code": "encounter-diagnosis",
          "display": "Encounter Diagnosis"
        }
      ]
    ]
  ],
  "severity": {
    "coding": [
      {
        "system": "http://hl7.org/fhir/sid/icd-10",
        "code": "24484000",
        "display": "Severe"
      }
    ],
    "text": "Severe"
  },
  "code": {
    "coding": [
      {
        "system": "http://hl7.org/fhir/sid/icd-10",
        "code": "A000",
        "display": "Cholera due to Vibrio cholerae 01, biovar cholerae"
      }
    ],
    "text": "Cholera due to Vibrio cholerae 01, biovar cholerae"
  },
  "subject": {
    "reference": "Patient/{patient id}"
  },
  "encounter": {
    "reference": "Encounter/{enocunter id}"
  },
  "onsetDateTime": "2024-05-01T09:00:00Z",
  "recordedDate": "2024-05-29",
  "recorder": {
    "reference": "Practitioner/{practitioner id}"
  }
}

```
