# Condition 
Condition resource is used to record symptoms and diagnoses made about the patient. It also includes health conditions that do not have a negative outcome, such as a pregnancy.

The line between using the `Condition` versus the `Observation` resource to capture symptoms is blurry; the general principle is to use the `Condition` resource when a symptom needs long-term management. For the sake of simplicity, Agni uses the `Condition` resource to log all symptoms.


## Resource Details
- FHIR R4 `Condition` resource: [https://hl7.org/fhir/R4/condition.html](https://hl7.org/fhir/R4/condition.html)

## Resource Example 
```json
{
    "resourceType": "Condition",
    "id": "uuid",
  "category": [
    {
      "coding": [
        {
          "system": "http://terminology.hl7.org/CodeSystem/condition-category",
          "code": "symptom-diagnosis",
          "display": "Symptom & Diagnosis"
        }
      ]
    }
  ],
    "code": {
        "coding": [
            {
                "system": "http://hl7.org/fhir/sid/icd-10",
                "code": "44054006",
                "display": "Typhoid fever with heart involvement"
            }
        ],
        "text": "Typhoid fever with heart involvement"
    },
    "subject": {
        "reference": "Patient/{patient id}"
    },
    "encounter": {
        "reference": "Encounter/{encounter id}"
    },
    "recorder": {
        "reference": "Practitioner/{practitioner id}"
    },
    "onsetDateTime": "2024-09-18T00:00:00Z",
    "evidence": [
        {
            "code": {
                "coding": [
                    {
                        "display": "Fever"
                    },
                    {
                        "display": "Headache"
                    }
                ]
            }
        }
    ]
}

```

