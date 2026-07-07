## Resource strucuture for medication dispense

### Prescribed
```json
{
                "resourceType": "MedicationDispense",
                "id": "3878",
                "meta": {
                    "versionId": "1",
                    "lastUpdated": "2024-12-04T04:03:27.920+00:00",
                    "source": "#RcoySMx0VOQm06mm"
                },
                "identifier": [
                    {
                        "type": {
                            "coding": [
                                {
                                    "system": "http://terminology.hl7.org/CodeSystem/v2-0203",
                                    "code": "MR"
                                }
                            ]
                        },
                        "system": "https://www.thelattice.in/",
                        "value": "063acf3c-287e-4bd1-843d-618fd588a705"
                    }
                ],
                "category": {
                    "coding": [
                        {
                            "system": "http://your-custom-coding-system",
                            "code": "prescribed"
                        }
                    ]
                },
                "medicationReference": {
                    "reference": "Medication/2170"
                },
                "subject": {
                    "reference": "Patient/3595"
                },
                "context": {
                    "reference": "Encounter/3877"
                },
                "authorizingPrescription": [
                    {
                        "reference": "MedicationRequest/3606"
                    }
                ],
                "quantity": {
                    "value": 2
                },
                "whenHandedOver": "2024-12-02T17:51:00+05:30",
                "substitution": {
                    "wasSubstituted": false
                }
            }
```

### OTC

```json
 {
                "resourceType": "MedicationDispense",
                "id": "3882",
                "meta": {
                    "versionId": "1",
                    "lastUpdated": "2024-12-04T04:05:38.306+00:00",
                    "source": "#AZpqfsUomGsIyyFp"
                },
                "identifier": [
                    {
                        "type": {
                            "coding": [
                                {
                                    "system": "http://terminology.hl7.org/CodeSystem/v2-0203",
                                    "code": "MR"
                                }
                            ]
                        },
                        "system": "https://www.thelattice.in/",
                        "value": "6824bb32-7d95-43fd-bf23-78191f3261db"
                    }
                ],
                "category": {
                    "coding": [
                        {
                            "system": "http://your-custom-coding-system",
                            "code": "OTC"
                        }
                    ]
                },
                "medicationReference": {
                    "reference": "Medication/2198"
                },
                "subject": {
                    "reference": "Patient/3595"
                },
                "context": {
                    "reference": "Encounter/3881"
                },
                "quantity": {
                    "value": 2
                },
                "whenHandedOver": "2024-12-02T17:51:00+05:30",
                "substitution": {
                    "wasSubstituted": false
                }
            }
```