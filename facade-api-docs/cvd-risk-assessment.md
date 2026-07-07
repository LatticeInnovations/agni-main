## CVD risk assessment

## Description
This section covers the flow of CVD risk assessment.

### Add assessment
1. Every assessment detail will have a separate Observation resource. We need to link it to the Encounter resource.
2. Encounter and Appointment for current data must be present before adding CVD assessment. This will be handled at android end.
3. When CVD assessment is added, we will create a sub encounter which will have reference of main encounter. Observation resources create will have reference of sub encounter only.

### Sub encounter resource
```
{
    "resourceType": "Encounter",
    "id": "2392",
    "meta": {
        "versionId": "1",
        "lastUpdated": "2024-10-27T04:30:24.591+00:00",
        "source": "#5GAqFxyl750CtKSU"
    },
    "identifier": [
        {
            "system": "http://hl7.org/fhir/sid/sn/vital",
            "value": "f2acef7b-3a27-4264-9f74-682bccb44a16"
        }
    ],
    "type": [
        {
            "coding": [
                {
                    "system": "http://your-custom-coding-system",
                    "code": "cvd-encounter",
                    "display": "CVD encounter"
                }
            ]
        }
    ],
    "subject": {
        "reference": "Patient/2361"
    },
    "participant": [
        {
            "individual": {
                "reference": "Practitioner/463"
            }
        }
    ],
    "period": {
        "start": "2024-09-17T09:50:02+05:30",
        "end": "2024-09-17T09:50:02+05:30"
    },
    "partOf": {
        "reference": "Encounter/2373",
        "display": "Primary Encounter"
    }
}
```

### Resources
**1. Encounter Resource**
- [Resource link](/fhir-resources/encounter.md)
- If there is no appointment keep the appointment section blank

**2. Observation resource**
- [Resource link](/fhir-resources/observation.md)
