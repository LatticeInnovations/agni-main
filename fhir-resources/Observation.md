---
order: 790
---

# Observation 
Observation resource is used to record vitals such as height, weight, respiratory rate, spO2, temperature, blood pressure, heart rate, blood glucose etc of the patient. Each observation resource is used to record the details of a single entity.

# Resource Details
> - We can refer to the [link](https://hl7.org/fhir/R4/observation.html) as well to check as per FHIR standard.
- We need to add a performer id of te logged in user in the resource as  well.

> Please use loinc code for filtering observation based on heart rate.
# Resource Example of Vitals

## Heart rate

```
{
  "resourceType": "Observation",
  "id": "uuid",
  "status": "final",
  "encounter": {
    "reference": "Encounter/{encounter id}"
  },
  "category": [
    {
      "coding": [
        {
          "system": "http://terminology.hl7.org/CodeSystem/observation-category",
          "code": "vital-signs",
          "display": "Vitals"
        }
      ]
    }
  ],
  "code": {
    "coding": [
      {
        "system": "http://loinc.org",
        "code": "8867-4",
        "display": "heartRate"
      }
    ]
  },
  "subject": {
    "reference": "Patient/12345"
  },
  "encounter": {
    "reference": "Encounter/67890"
  },
  "effectiveDateTime": "2024-09-19T10:30:00Z"
  "component": [
    {
      "code": {
        "coding": [
          {
            "system": "http://loinc.org",
            "code": "8867-4",
            "display": "Heart rate"
      }
        ]
      },
      "valueQuantity": {
        "value": 72,
        "unit": "beats/minute",
        "system": "http://unitsofmeasure.org",
        "code": "/min"
  }
    }
  ]
}
```

## Blood pressure

```
{
  "resourceType": "Observation",
  "id": "uuid",
  "status": "final",
  "encounter": {
    "reference": "Encounter/{encounter id}"
  },
  "category": [
    {
      "coding": [
        {
          "system": "http://terminology.hl7.org/CodeSystem/observation-category",
          "code": "vital-signs",
          "display": "Vitals"
        }
      ]
    }
  ],
  "code": {
    "coding": [
      {
        "system": "http://loinc.org",
        "code": "35094-2",
        "display": "Blood Pressure"
      }
    ]
  },
  "subject": {
    "reference": "Patient/12345"
  },
  "encounter": {
    "reference": "Encounter/67890"
  },
  "effectiveDateTime": "2024-09-19T10:30:00Z",
  "component": [
    {
      "code": {
        "coding": [
          {
            "system": "http://loinc.org",
            "code": "8480-6",
            "display": "Systolic blood pressure"
          }
        ]
      },
      "valueQuantity": {
        "value": 120,
        "unit": "mmHg",
        "system": "http://unitsofmeasure.org",
        "code": "mm[Hg]"
      }
    },
    {
      "code": {
        "coding": [
          {
            "system": "http://loinc.org",
            "code": "8462-4",
            "display": "Diastolic blood pressure"
          }
        ]
      },
      "valueQuantity": {
        "value": 80,
        "unit": "mmHg",
        "system": "http://unitsofmeasure.org",
        "code": "mm[Hg]"
      }
    }
  ],
}
```

## Temperature
```
{
  "resourceType": "Observation",
  "id": "uuid",
  "encounter": {
    "reference": "Encounter/67890"
  }
  "status": "final",
  "category": [
    {
      "coding": [
        {
          "system": "http://terminology.hl7.org/CodeSystem/observation-category",
          "code": "vital-signs",
          "display": "Vitals"
        }
      ]
    }
  ],
  "code": {
    "coding": [
      {
        "system": "http://loinc.org",
        "code": "8310-5",
        "display": "temperature"
      }
    ]
  },
  "component": [
    {
      "code": {
        "coding": [
          {
        "system": "http://loinc.org",
        "code": "8310-5",
        "display": "Body temperature"
      }
        ]
      },
      "valueQuantity": {
        "value": 98.6,
        "unit": "degrees Fahrenheit",
        "system": "http://unitsofmeasure.org",
        "code": "[degF]"
      }
    }
  ]
  "subject": {
    "reference": "Patient/12345",
    "display": "John Doe"
  },
  "effectiveDateTime": "2024-09-19T10:30:00Z"
  }
```
## Glucose

```
{
  "resourceType": "Observation",
  "id": "uuid",
  "status": "final",
  "encounter": {
    "reference": "Encounter/67890"
  }
  "category": [
    {
      "coding": [
        {
          "system": "http://terminology.hl7.org/CodeSystem/observation-category",
          "code": "vital-signs",
          "display": "Vitals"
        }
      ]
    }
  ],
  "code": {
    "coding": [
      {
        "system": "http://loinc.org",
        "code": "74774-1",
        "display": "glucose"
      }
    ]
  },
  "subject": {
    "reference": "Patient/12345"
  },
  "component": [
    {
      "code": {
        "coding": [
          {
            "system": "http://loinc.org",
            "code": "1558-6",
            "display": "fasting"
          }
        ],
        "text": "Fasting Blood Glucose"
      },
      "valueQuantity": {
        "value": 90,
        "unit": "mg/dL",
        "system": "http://unitsofmeasure.org",
        "code": "mg/dL"
      }
    },
    {
      "code": {
        "coding": [
          {
            "system": "http://loinc.org",
            "code": "74774-1",
            "display": "random"
          }
        ],
        "text": "Random Blood Glucose"
      },
      "valueQuantity": {
        "value": 110,
        "unit": "mg/dL",
        "system": "http://unitsofmeasure.org",
        "code": "mg/dL"
      }
    }
  ]
}
```

## Height
```
{
  "resourceType": "Observation",
  "id": "height-observation",
  "status": "final",
  "category": [
    {
      "coding": [
        {
          "system": "http://terminology.hl7.org/CodeSystem/observation-category",
          "code": "vital-signs",
          "display": "Vitals"
        }
      ]
    }
  ],
  "code": {
    "coding": [
      {
        "system": "http://loinc.org",
        "code": "8302-2",
        "display": "height"
      }
    ]
  },
  "subject": {
    "reference": "Patient/12345
  },
  "effectiveDateTime": "2024-09-19T09:00:00Z",
  "component": [
    {
      "code": {
        "coding": [
          {
            "system": "http://loinc.org",
            "code": "8302-2",
            "display": "height"
          }
        ],
        "text": "Height in feet"
      },
      "valueQuantity": {
        "value": 5,
        "unit": "ft",
        "system": "http://unitsofmeasure.org",
        "code": "[ft_i]"
      }
    },
    {
      "code": {
        "coding": [
          {
            "system": "http://loinc.org",
            "code": "8302-2",
            "display": "height"
          }
        ],
        "text": "Height in inches"
      },
      "valueQuantity": {
        "value": 9,
        "unit": "in",
        "system": "http://unitsofmeasure.org",
        "code": "[in_i]"
      }
    }
  ]
}

```

## Weight
```
{
  "resourceType": "Observation",
  "id": "uuid",
  "status": "final",
  "category": [
    {
      "coding": [
        {
          "system": "http://terminology.hl7.org/CodeSystem/observation-category",
          "code": "vital-signs",
          "display": "Vitals"
        }
      ]
    }
  ],
  "code": {
    "coding": [
      {
        "system": "http://loinc.org",
        "code": "29463-7",
        "display": "weight"
      }
    ]
  },
  "subject": {
    "reference": "Patient/12345",
    "display": "John Doe"
  },
  "effectiveDateTime": "2024-09-19T09:00:00Z",
    "component": [
    {
      "code": {
        "coding": [
          {
            "system": "http://loinc.org",
            "code": "29463-7",
            "display": "weight"
          }
        ]
      },
      "valueQuantity": {
        "value": 70,
        "unit": "kg",
        "system": "http://unitsofmeasure.org",
        "code": "kg"
    }
    }
  ]
}
```



# Resource Example of CVD risk assessment

## Diabetic Status

```
{
  "resourceType": "Observation",
  "id": "45179171",
  "status": "final",
  "encounter": {
    "reference": "Encounter/67890"
  }
  "category": [
    {
      "coding": [
        {
          "system": "http://terminology.hl7.org/CodeSystem/observation-category",
          "code": "CVD",
          "display": "CVD risk assessment"
        }
      ]
    }
  ],
  "code": {
        "coding": [
            {
                "system": "http://loinc.org",
                "code": "44069-8",
                "display": "Diabetic status"
            }
        ],
        "text": "Diabetic status"
  },
  "effectiveDateTime": "2024-09-19T10:30:00Z",
  "subject": {
    "reference": "Patient/12345
  },
  "performer": [
        {
            "reference": "Practitioner/463"
        }
    ],
  "component": [
    {
      "code": {
        "coding": [
          {
            "system": "http://loinc.org",
            "code": "33248-6",
            "display": "Diabetic status"
          }
        ],
       "text": "Diabetic status"
      },
      "valueQuantity": {
        "value": 1,  // if 1 then diabetic, if 0 then non diabetic
        "system": "http://unitsofmeasure.org"
      }
    }
  ]
}
```

## Smoking status : 

```
{
  "resourceType": "Observation",
  "id": "45179172",
  "status": "final",
  "encounter": {
    "reference": "Encounter/67890"
  },
  "category": [
    {
      "coding": [
        {
                    "system": "http://terminology.hl7.org/CodeSystem/observation-category",
                    "code": "CVD",
                    "display": "CVD risk assessment"
                }
      ]
    }
  ],
  "code": {
        "coding": [
            {
                "system": "http://loinc.org",
                "code": "72166-2",
                "display": "smoking status"
            }
        ],
        "text": "Smoking Status"
  },
  "effectiveDateTime": "2024-09-19T10:30:00Z",
  "subject": {
    "reference": "Patient/12345"
  },
  "performer": [
        {
            "reference": "Practitioner/463"
        }
  ],
  "component": [
    {
      "code": {
        "coding": [
          {
            "system": "http://loinc.org",
            "code": "72166-2",
            "display": "smoking status"
          }
        ],
        "text": "Smoking Status"
      },
      "valueQuantity": {
        "value": 1,  // if 1 then smoker, if 0 then non-smoker
        "system": "http://unitsofmeasure.org"
      }
    }
  ]
}

```

## Blood Pressure

```
{
    "resourceType": "Observation",
    "id": "2708",
    "meta": {
        "versionId": "1",
        "lastUpdated": "2024-10-27T05:26:59.887+00:00",
        "source": "#Go0WOoeqGeT6a7Pr"
    },
    "status": "final",
    "category": [
        {
            "coding": [
                {
                    "system": "http://terminology.hl7.org/CodeSystem/observation-category",
                    "code": "CVD",
                    "display": "CVD risk assessment"
                }
            ]
        }
    ],
    "code": {
        "coding": [
            {
              "system": "http://loinc.org",
              "code": "35094-2",
              "display": "Blood Pressure"
      }
        ],
        "text": "Blood Pressure"
    },
    "subject": {
        "reference": "Patient/2361"
    },
    "encounter": {
        "reference": "Encounter/2701"
    },
    "effectiveDateTime": "2024-08-23T10:55:12+05:30",
    "performer": [
        {
            "reference": "Practitioner/463"
        }
    ],
    "component": [
        {
            "code": {
                "coding": [
                    {
                        "system": "http://loinc.org",
                        "code": "8462-4",
                        "display": "Diastolic blood pressure"
                    }
                ],
                "text": "Diastolic blood pressure"
            },
            "valueQuantity": {
                "value": 21,
                "unit": "mmHg",
                "system": "http://unitsofmeasure.org",
                "code": "mm[Hg]"
            }
        },
        {
            "code": {
                "coding": [
                    {
                        "system": "http://loinc.org",
                        "code": "8480-6",
                        "display": "Systolic blood pressure"
                    }
                ],
                "text": "Systolic blood pressure"
            },
            "valueQuantity": {
                "value": 36,
                "unit": "mmHg",
                "system": "http://unitsofmeasure.org",
                "code": "mm[Hg]"
            }
        }
    ]
}
```

## Cholesterol

```
{
    "resourceType": "Observation",
    "id": "2708",
    "meta": {
        "versionId": "1",
        "lastUpdated": "2024-10-27T05:26:59.887+00:00",
        "source": "#Go0WOoeqGeT6a7Pr"
    },
    "status": "final",
    "category": [
        {
            "coding": [
                {
                    "system": "http://terminology.hl7.org/CodeSystem/observation-category",
                    "code": "CVD
                    "display": "CVD risk assessment"
                }
            ]
        }
    ],
    "code": {
        "coding": [
            {
                "system": "http://loinc.org",
                "code": "2093-3",
                "display": "Cholesterol [Mass/volume] in Serum or Plasma"
            }
        ],
        "text": "Cholesterol"
    },
    "subject": {
        "reference": "Patient/2361"
    },
    "encounter": {
        "reference": "Encounter/2701"
    },
    "effectiveDateTime": "2024-08-23T10:55:12+05:30",
    "performer": [
        {
            "reference": "Practitioner/463"
        }
    ],
    "component": [
        {
            "code": {
                "coding": [
                    {
                        "system": "http://loinc.org",
                        "code": "2093-3",
                        "display": "Cholesterol [Mass/volume] in Serum or Plasma"
                    }
                ],
                "text": "Cholesterol"
            },
            "valueQuantity": {
                "value": 5.2,
                "unit": "mmol/L", // change if mg/dl
                "system": "http://unitsofmeasure.org",
                "code": "mmol/L" // change if mg/dl
            }
        }
    ]
}
```

## Height : 
```
{
    "resourceType": "Observation",
    "id": "2393",
    "meta": {
        "versionId": "1",
        "lastUpdated": "2024-10-27T04:30:24.591+00:00",
        "source": "#5GAqFxyl750CtKSU"
    },
    "status": "final",
    "category": [
        {
            "coding": [
                {
                    "system": "http://terminology.hl7.org/CodeSystem/observation-category",
                    "code": "CVD",
                    "display": "CVD risk assessment"
                }
            ]
        }
    ],
    "code": {
        "coding": [
            {
                "system": "http://loinc.org",
                "code": "8302-2",
                "display": "height"
            }
        ],
        "text": "Height"
    },
    "subject": {
        "reference": "Patient/2361"
    },
    "encounter": {
        "reference": "Encounter/2392"
    },
    "effectiveDateTime": "2024-09-17T09:50:02+05:30",
    "performer": [
        {
            "reference": "Practitioner/463"
        }
    ],
    "component": [
        {
            "code": {
                "coding": [
                    {
                        "system": "http://loinc.org",
                        "code": "8302-2",
                        "display": "feet"
                    }
                ],
                "text": "Height in feet"
            },
            "valueQuantity": {
                "value": 5,
                "unit": "ft",
                "system": "http://unitsofmeasure.org",
                "code": "[ft_i]"
            }
        },
        {
            "code": {
                "coding": [
                    {
                        "system": "http://loinc.org",
                        "code": "8302-2",
                        "display": "inches"
                    }
                ],
                "text": "Height in inches"
            },
            "valueQuantity": {
                "value": 5,
                "unit": "in",
                "system": "http://unitsofmeasure.org",
                "code": "[in_i]"
            }
        }
    ]
}
```

## Weight : 

```
{
    "resourceType": "Observation",
    "id": "2404",
    "meta": {
        "versionId": "1",
        "lastUpdated": "2024-10-27T04:30:24.591+00:00",
        "source": "#5GAqFxyl750CtKSU"
    },
    "status": "final",
    "category": [
        {
            "coding": [
                {
                    "system": "http://terminology.hl7.org/CodeSystem/observation-category",
                    "code": "CVD",
                    "display": "CVD risk assessment"
                }
            ]
        }
    ],
    "code": {
        "coding": [
            {
                "system": "http://loinc.org",
                "code": "29463-7",
                "display": "weight"
            }
        ],
        "text": "Weight"
    },
    "subject": {
        "reference": "Patient/2361"
    },
    "encounter": {
        "reference": "Encounter/2402"
    },
    "effectiveDateTime": "2024-09-30T09:51:53+05:30",
    "performer": [
        {
            "reference": "Practitioner/463"
        }
    ],
    "component": [
        {
            "code": {
                "coding": [
                    {
                        "system": "http://loinc.org",
                        "code": "29463-7",
                        "display": "weight"
                    }
                ],
                "text": "Weight"
            },
            "valueQuantity": {
                "value": 36,
                "unit": "kg",
                "system": "http://unitsofmeasure.org",
                "code": "kg"
            }
        }
    ]
}
```


## BMI

```
{
    "resourceType": "Observation",
    "id": "2404",
    "meta": {
        "versionId": "1",
        "lastUpdated": "2024-10-27T04:30:24.591+00:00",
        "source": "#5GAqFxyl750CtKSU"
    },
    "status": "final",
    "category": [
        {
            "coding": [
                {
                    "system": "http://terminology.hl7.org/CodeSystem/observation-category",
                    "code": "CVD",
                    "display": "CVD risk assessment"
                }
            ]
        }
    ],
    "code": {
        "coding": [
            {
                "system": "http://loinc.org",
                "code": "9156-5",
                "display": "Body mass index (BMI) [Ratio]"
            }
        ],
        "text": "BMI"
    },
    "subject": {
        "reference": "Patient/2361"
    },
    "encounter": {
        "reference": "Encounter/2402"
    },
    "effectiveDateTime": "2024-09-30T09:51:53+05:30",
    "performer": [
        {
            "reference": "Practitioner/463"
        }
    ],
    "component": [
        {
            "code": {
                "coding": [
                    {
                        "system": "http://loinc.org",
                        "code": "9156-5",
                        "display": "Body mass index (BMI) [Ratio]"
                    }
                ],
                "text": "BMI"
            },
            "valueQuantity": {
                "value": 22.5,
                "unit": "kg/m2",
                "system": "http://unitsofmeasure.org",
                "code": "kg/m2"
            }
        }
    ]
}
```

## CVD Risk percentage : 

```
{
    "resourceType": "Observation",
    "id": "2505",
    "status": "final",
    "category": [
        {
            "coding": [
                {
                    "system": "http://terminology.hl7.org/CodeSystem/observation-category",
                    "code": "CVD",
                    "display": "CVD risk assessment"
                }
            ]
        }
    ],
    "code": {
        "coding": [
            {
                "system": "http://loinc.org",
                "code": "72333-9",
                "display": "Cardiovascular disease risk score"
            }
        ],
        "text": "CVD Risk Percentage"
    },
    "subject": {
        "reference": "Patient/2361"
    },
    "encounter": {
        "reference": "Encounter/2402"
    },
    "effectiveDateTime": "2024-11-19T10:00:00+05:30",
    "performer": [
        {
            "reference": "Practitioner/463"
        }
    ],
    "component": [
        {
            "code": {
               "coding": [
                  {
                      "system": "http://loinc.org",
                      "code": "72333-9",
                      "display": "Cardiovascular disease risk score"
                  }
                ],
                "text": "CVD Risk Percentage"
            },
            "valueQuantity": {
                "value": 15.3,
                "unit": "%",
                "system": "http://unitsofmeasure.org",
                "code": "%"
            }
        }
    ]
}

```
