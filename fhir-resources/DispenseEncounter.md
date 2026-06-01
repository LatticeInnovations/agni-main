# DispenseEncounter
## Main dispense encounter for prescribed data

```json
 {
            "fullUrl": "http://example.url/fhir/Encounter/3876",
            "resource": {
                "resourceType": "Encounter",
                "id": "3876",
                "meta": {
                    "versionId": "1",
                    "lastUpdated": "2024-12-04T04:03:27.920+00:00",
                    "source": "#RcoySMx0VOQm06mm"
                },
                "identifier": [
                    {
                        "system": "http://hl7.org/fhir/sid/sn",
                        "value": "d9859f58-3f53-4e16-a3cc-1d9e8002aa8e"
                    }
                ],
                "status": "in-progress",
                "type": [
                    {
                        "coding": [
                            {
                                "system": "http://your-custom-coding-system",
                                "code": "pharmacy-service",
                                "display": "Pharmacy service"
                            }
                        ]
                    }
                ],
                "subject": {
                    "reference": "Patient/3595"
                },
                "period": {
                    "start": "2024-12-02T17:51:00+05:30",
                    "end": "2024-12-02T17:51:00+05:30"
                },
                "partOf": {
                    "reference": "Encounter/3605"
                }
            },
            "search": {
                "mode": "match"
            }
        }
```

### Sub encounter for prescribed
```json
{
                "resourceType": "Encounter",
                "id": "3877",
                "meta": {
                    "versionId": "1",
                    "lastUpdated": "2024-12-04T04:03:27.920+00:00",
                    "source": "#RcoySMx0VOQm06mm"
                },
                "extension": [
                    {
                        "url": "http://hl7.org/fhir/StructureDefinition/encounter-note",
                        "valueString": "Please go for a walk"
                    }
                ],
                "identifier": [
                    {
                        "system": "http://hl7.org/fhir/sid/sn",
                        "value": "05cd9233-9695-487b-8023-016969728e9c"
                    }
                ],
                "type": [
                    {
                        "coding": [
                            {
                                "system": "http://your-custom-coding-system",
                                "code": "dispensing-encounter",
                                "display": "Dispensing encounter"
                            }
                        ]
                    }
                ],
                "subject": {
                    "reference": "Patient/3595"
                },
                "period": {
                    "start": "2024-12-02T17:51:00+05:30",
                    "end": "2024-12-02T17:51:00+05:30"
                },
                "partOf": {
                    "reference": "Encounter/3876"
                }
            }
```

### Sub encounter for OTC

```json
{
                "resourceType": "Encounter",
                "id": "3881",
                "meta": {
                    "versionId": "1",
                    "lastUpdated": "2024-12-04T04:05:38.306+00:00",
                    "source": "#AZpqfsUomGsIyyFp"
                },
                "identifier": [
                    {
                        "system": "http://hl7.org/fhir/sid/sn",
                        "value": "247798aa-e1a7-42bf-a74e-f1ef9a7dc3d1"
                    }
                ],
                "type": [
                    {
                        "coding": [
                            {
                                "system": "http://your-custom-coding-system",
                                "code": "dispensing-encounter",
                                "display": "Dispensing encounter"
                            }
                        ]
                    }
                ],
                "subject": {
                    "reference": "Patient/3595"
                },
                "period": {
                    "start": "2024-12-02T17:51:00+05:30",
                    "end": "2024-12-02T17:51:00+05:30"
                }
            }
```