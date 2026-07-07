# ImmunizationRecommendation 
This resource will be used to store Vaccine Recommendation data for a particular patient.

# Resource Details
> - We can refer to the [link](https://hl7.org/fhir/immunizationrecommendation.html) as well to check as per FHIR standard

- `authority` field in this resource will refer to the Organization of the Practitioner.

# Resource Example 
## Bacillus Calmette-Guerin vaccine
```javascript
{
  "resourceType": "ImmunizationRecommendation",
  "id": "1",
  "patient": {
    "reference": "Patient/1"
  },
  "date": "2025-02-25",
  "authority": {
    "reference": "Organization/2",  
  },
  "recommendation": [
    {
      "vaccineCode": [
        {
          "coding": [
            {
              "system": "http://hl7.org/fhir/sid/cvx",
              "code": "19",
              "display": "Bacillus Calmette-Guerin vaccine"
            }
          ],
          "text": "BCG"
        }
      ],
      "dateCriterion": [
        {
          "code": {
            "coding": [
              {
                "system": "http://loinc.org/",
                "code": "30981-5",
                "display": "Earliest date to give"
              }
            ]
          },
          "value": "2025-02-28"
        },
        {
          "code": {
            "coding": [
              {
                "system": "http://loinc.org/",
                "code": "30980-7",
                "display": "Date vaccine due"
              }
            ]
          },
          "value": "2025-03-10"
        },
        {
          "code": {
            "coding": [
              {
                "system": "http://loinc.org/",
                "code": "59778-1",
                "display": "Date when overdue for immunization"
              }
            ]
          },
          "value": "2025-04-10"
        }
      ],
      "doseNumberString": "1",
      "seriesDosesString": "1",
      "supportingImmunization": [
        {
          "reference": "Immunization/3"
        }
      ]
    }
  ]
}

```

## hepatitis B vaccine, pediatric or pediatric/adolescent dosage
```javascript
{
  "resourceType": "ImmunizationRecommendation",
  "id": "1",
  "patient": {
    "reference": "Patient/1"
  },
  "date": "2025-02-25",
  "authority": {
    "reference": "Organization/2",
  },
  "recommendation": [
    {
      "vaccineCode": [
        {
          "coding": [
            {
              "system": "http://hl7.org/fhir/sid/cvx",
              "code": "45",
              "display": "hepatitis B vaccine, pediatric or pediatric/adolescent dosage"
            }
          ],
          "text": "Hep B, adolescent or pediatric"
        }
      ],
      "dateCriterion": [
        {
          "code": {
            "coding": [
              {
                "system": "http://loinc.org/",
                "code": "30981-5",
                "display": "Earliest date to give"
              }
            ]
          },
          "value": "2025-02-28"
        },
        {
          "code": {
            "coding": [
              {
                "system": "http://loinc.org/",
                "code": "30980-7",
                "display": "Date vaccine due"
              }
            ]
          },
          "value": "2025-03-10"
        },
        {
          "code": {
            "coding": [
              {
                "system": "http://loinc.org/",
                "code": "59777-1",
                "display": "Latest date to give immunization"
              }
            ]
          },
          "value": "2025-04-10"
        }
      ],
      "doseNumberString": "1",
      "seriesDosesString": "4",
      "supportingImmunization": [
        {
          "reference": "Immunization/3"
        }
      ]
    },
    {
      "vaccineCode": [
        {
          "coding": [
            {
              "system": "http://hl7.org/fhir/sid/cvx",
              "code": "45",
              "display": "hepatitis B vaccine, pediatric or pediatric/adolescent dosage"
            }
          ],
          "text": "Hep B, adolescent or pediatric"
        }
      ],
      "dateCriterion": [
        {
          "code": {
            "coding": [
              {
                "system": "http://loinc.org/",
                "code": "30981-5",
                "display": "Earliest date to give"
              }
            ]
          },
          "value": "2025-02-28"
        },
        {
          "code": {
            "coding": [
              {
                "system": "http://loinc.org/",
                "code": "30980-7",
                "display": "Date vaccine due"
              }
            ]
          },
          "value": "2025-03-10"
        },
        {
          "code": {
            "coding": [
              {
                "system": "http://loinc.org/",
                "code": "59778-1",
                "display": "Date when overdue for immunization"
              }
            ]
          },
          "value": "2025-04-10"
        }
      ],
      "doseNumberString": "2",
      "seriesDosesString": "4",
      "supportingImmunization": [
        {
          "reference": "Immunization/5"
        }
      ]
    },
    {
      "vaccineCode": [
        {
          "coding": [
            {
              "system": "http://hl7.org/fhir/sid/cvx",
              "code": "45",
              "display": "hepatitis B vaccine, pediatric or pediatric/adolescent dosage"
            }
          ],
          "text": "Hep B, adolescent or pediatric"
        }
      ],
      "dateCriterion": [
        {
          "code": {
            "coding": [
              {
                "system": "http://loinc.org/",
                "code": "30981-5",
                "display": "Earliest date to give"
              }
            ]
          },
          "value": "2025-02-28"
        },
        {
          "code": {
            "coding": [
              {
                "system": "http://loinc.org/",
                "code": "30980-7",
                "display": "Date vaccine due"
              }
            ]
          },
          "value": "2025-03-10"
        },
        {
          "code": {
            "coding": [
              {
                "system": "http://loinc.org/",
                "code": "59777-1",
                "display": "Latest date to give immunization"
              }
            ]
          },
          "value": "2025-04-10"
        }
      ],
      "doseNumberString": "3",
      "seriesDosesString": "4",
      "supportingImmunization": [
        {
          "reference": "Immunization/3"
        }
      ]
    },
    {
      "vaccineCode": [
        {
          "coding": [
            {
              "system": "http://hl7.org/fhir/sid/cvx",
              "code": "45",
              "display": "hepatitis B vaccine, pediatric or pediatric/adolescent dosage"
            }
          ],
          "text": "Hep B, adolescent or pediatric"
        }
      ],
      "dateCriterion": [
        {
          "code": {
            "coding": [
              {
                "system": "http://loinc.org/",
                "code": "30981-5",
                "display": "Earliest date to give"
              }
            ]
          },
          "value": "2025-02-28"
        },
        {
          "code": {
            "coding": [
              {
                "system": "http://loinc.org/",
                "code": "30980-7",
                "display": "Date vaccine due"
              }
            ]
          },
          "value": "2025-03-10"
        },
        {
          "code": {
            "coding": [
              {
                "system": "http://loinc.org/",
                "code": "59777-1",
                "display": "Latest date to give immunization"
              }
            ]
          },
          "value": "2025-04-10"
        }
      ],
      "doseNumberString": "4",
      "seriesDosesString": "4",
      "supportingImmunization": [
        {
          "reference": "Immunization/3"
        }
      ]
    }
  ]
}

```

## trivalent poliovirus vaccine, live, oral

```javascript
{
  "resourceType": "ImmunizationRecommendation",
  "id": "1",
  "patient": {
    "reference": "Patient/1"
  },
  "date": "2025-02-25",
  "authority": {
    "reference": "Organization/2",
    
  },
  "recommendation": [
    {
      "vaccineCode": [
        {
          "coding": [
            {
              "system": "http://hl7.org/fhir/sid/cvx",
              "code": "2",
              "display": "trivalent poliovirus vaccine, live, oral"
            }
          ],
          "text": "OPV"
        }
      ],
      "dateCriterion": [
        {
          "code": {
            "coding": [
              {
                "system": "http://loinc.org/",
                "code": "30981-5",
                "display": "Earliest date to give"
              }
            ]
          },
          "value": "2025-02-28"
        },
        {
          "code": {
            "coding": [
              {
                "system": "http://loinc.org/",
                "code": "30980-7",
                "display": "Date vaccine due"
              }
            ]
          },
          "value": "2025-03-10"
        },
        {
          "code": {
            "coding": [
              {
                "system": "http://loinc.org/",
                "code": "59778-1",
                "display": "Date when overdue for immunization"
              }
            ]
          },
          "value": "2025-04-10"
        }
      ],
      "doseNumberString": "1",
      "seriesDosesString": "1",
      "supportingImmunization": [
        {
          "reference": "Immunization/3"
        }
      ]
    }
  ]
}

```

## poliovirus vaccine, inactivated

```javascript
{
  "resourceType": "ImmunizationRecommendation",
  "id": "1",
  "patient": {
    "reference": "Patient/1"
  },
  "date": "2025-02-25",
  "authority": {
    "reference": "Organization/2",
    
  },
  "recommendation": [
    {
      "vaccineCode": [
        {
          "coding": [
            {
              "system": "http://hl7.org/fhir/sid/cvx",
              "code": "10",
              "display": "poliovirus vaccine, inactivated"
            }
          ],
          "text": "IPV"
        }
      ],
      "dateCriterion": [
        {
          "code": {
            "coding": [
              {
                "system": "http://loinc.org/",
                "code": "30981-5",
                "display": "Earliest date to give"
              }
            ]
          },
          "value": "2025-02-28"
        },
        {
          "code": {
            "coding": [
              {
                "system": "http://loinc.org/",
                "code": "30980-7",
                "display": "Date vaccine due"
              }
            ]
          },
          "value": "2025-03-10"
        },
        {
          "code": {
            "coding": [
              {
                "system": "http://loinc.org/",
                "code": "59778-1",
                "display": "Date when overdue for immunization"
              }
            ]
          },
          "value": "2025-04-10"
        }
      ],
      "doseNumberString": "1",
      "seriesDosesString": "5",
      "supportingImmunization": [
        {
          "reference": "Immunization/3"
        }
      ]
    },
    {
      "vaccineCode": [
        {
          "coding": [
            {
              "system": "http://hl7.org/fhir/sid/cvx",
              "code": "10",
              "display": "poliovirus vaccine, inactivated"
            }
          ],
          "text": "IPV"
        }
      ],
      "dateCriterion": [
        {
          "code": {
            "coding": [
              {
                "system": "http://loinc.org/",
                "code": "30981-5",
                "display": "Earliest date to give"
              }
            ]
          },
          "value": "2025-02-28"
        },
        {
          "code": {
            "coding": [
              {
                "system": "http://loinc.org/",
                "code": "30980-7",
                "display": "Date vaccine due"
              }
            ]
          },
          "value": "2025-03-10"
        },
        {
          "code": {
            "coding": [
              {
                "system": "http://loinc.org/",
                "code": "59778-1",
                "display": "Date when overdue for immunization"
              }
            ]
          },
          "value": "2025-04-10"
        }
      ],
      "doseNumberString": "2",
      "seriesDosesString": "5",
      "supportingImmunization": [
        {
          "reference": "Immunization/3"
        }
      ]
    },
    {
      "vaccineCode": [
        {
          "coding": [
            {
              "system": "http://hl7.org/fhir/sid/cvx",
              "code": "10",
              "display": "poliovirus vaccine, inactivated"
            }
          ],
          "text": "IPV"
        }
      ],
      "dateCriterion": [
        {
          "code": {
            "coding": [
              {
                "system": "http://loinc.org/",
                "code": "30981-5",
                "display": "Earliest date to give"
              }
            ]
          },
          "value": "2025-02-28"
        },
        {
          "code": {
            "coding": [
              {
                "system": "http://loinc.org/",
                "code": "30980-7",
                "display": "Date vaccine due"
              }
            ]
          },
          "value": "2025-03-10"
        },
        {
          "code": {
            "coding": [
              {
                "system": "http://loinc.org/",
                "code": "59778-1",
                "display": "Date when overdue for immunization"
              }
            ]
          },
          "value": "2025-04-10"
        }
      ],
      "doseNumberString": "3",
      "seriesDosesString": "5",
      "supportingImmunization": [
        {
          "reference": "Immunization/3"
        }
      ]
    },
    {
      "vaccineCode": [
        {
          "coding": [
            {
              "system": "http://hl7.org/fhir/sid/cvx",
              "code": "10",
              "display": "poliovirus vaccine, inactivated"
            }
          ],
          "text": "IPV"
        }
      ],
      "dateCriterion": [
        {
          "code": {
            "coding": [
              {
                "system": "http://loinc.org/",
                "code": "30981-5",
                "display": "Earliest date to give"
              }
            ]
          },
          "value": "2025-02-28"
        },
        {
          "code": {
            "coding": [
              {
                "system": "http://loinc.org/",
                "code": "30980-7",
                "display": "Date vaccine due"
              }
            ]
          },
          "value": "2025-03-10"
        },
        {
          "code": {
            "coding": [
              {
                "system": "http://loinc.org/",
                "code": "59778-1",
                "display": "Date when overdue for immunization"
              }
            ]
          },
          "value": "2025-04-10"
        }
      ],
      "doseNumberString": "4",
      "seriesDosesString": "5",
      "supportingImmunization": [
        {
          "reference": "Immunization/3"
        }
      ]
    },
    {
      "vaccineCode": [
        {
          "coding": [
            {
              "system": "http://hl7.org/fhir/sid/cvx",
              "code": "10",
              "display": "poliovirus vaccine, inactivated"
            }
          ],
          "text": "IPV"
        }
      ],
      "dateCriterion": [
        {
          "code": {
            "coding": [
              {
                "system": "http://loinc.org/",
                "code": "30981-5",
                "display": "Earliest date to give"
              }
            ]
          },
          "value": "2025-02-28"
        },
        {
          "code": {
            "coding": [
              {
                "system": "http://loinc.org/",
                "code": "30980-7",
                "display": "Date vaccine due"
              }
            ]
          },
          "value": "2025-03-10"
        },
        {
          "code": {
            "coding": [
              {
                "system": "http://loinc.org/",
                "code": "59778-1",
                "display": "Date when overdue for immunization"
              }
            ]
          },
          "value": "2025-04-10"
        }
      ],
      "doseNumberString": "5",
      "seriesDosesString": "5",
      "supportingImmunization": [
        {
          "reference": "Immunization/3"
        }
      ]
    }
  ]
}

```

## diphtheria, tetanus toxoids and acellular pertussis vaccine

```javascript
{
  "resourceType": "ImmunizationRecommendation",
  "id": "1",
  "patient": {
    "reference": "Patient/1"
  },
  "date": "2025-02-25",
  "authority": {
    "reference": "Organization/2",
    
  },
  "recommendation": [
    {
      "vaccineCode": [
        {
          "coding": [
            {
              "system": "http://hl7.org/fhir/sid/cvx",
              "code": "20",
              "display": "diphtheria, tetanus toxoids and acellular pertussis vaccine"
            }
          ],
          "text": "DTaP"
        }
      ],
      "dateCriterion": [
        {
          "code": {
            "coding": [
              {
                "system": "http://loinc.org/",
                "code": "30981-5",
                "display": "Earliest date to give"
              }
            ]
          },
          "value": "2025-02-28"
        },
        {
          "code": {
            "coding": [
              {
                "system": "http://loinc.org/",
                "code": "30980-7",
                "display": "Date vaccine due"
              }
            ]
          },
          "value": "2025-03-10"
        },
        {
          "code": {
            "coding": [
              {
                "system": "http://loinc.org/",
                "code": "59778-1",
                "display": "Date when overdue for immunization"
              }
            ]
          },
          "value": "2025-04-10"
        }
      ],
      "doseNumberString": "1",
      "seriesDosesString": "5",
      "supportingImmunization": [
        {
          "reference": "Immunization/3"
        }
      ]
    },
    {
      "vaccineCode": [
        {
          "coding": [
            {
              "system": "http://hl7.org/fhir/sid/cvx",
              "code": "20",
              "display": "diphtheria, tetanus toxoids and acellular pertussis vaccine"
            }
          ],
          "text": "DTaP"
        }
      ],
      "dateCriterion": [
        {
          "code": {
            "coding": [
              {
                "system": "http://loinc.org/",
                "code": "30981-5",
                "display": "Earliest date to give"
              }
            ]
          },
          "value": "2025-02-28"
        },
        {
          "code": {
            "coding": [
              {
                "system": "http://loinc.org/",
                "code": "30980-7",
                "display": "Date vaccine due"
              }
            ]
          },
          "value": "2025-03-10"
        },
        {
          "code": {
            "coding": [
              {
                "system": "http://loinc.org/",
                "code": "59778-1",
                "display": "Date when overdue for immunization"
              }
            ]
          },
          "value": "2025-04-10"
        }
      ],
      "doseNumberString": "2",
      "seriesDosesString": "5",
      "supportingImmunization": [
        {
          "reference": "Immunization/3"
        }
      ]
    },
    {
      "vaccineCode": [
        {
          "coding": [
            {
              "system": "http://hl7.org/fhir/sid/cvx",
              "code": "20",
              "display": "diphtheria, tetanus toxoids and acellular pertussis vaccine"
            }
          ],
          "text": "DTaP"
        }
      ],
      "dateCriterion": [
        {
          "code": {
            "coding": [
              {
                "system": "http://loinc.org/",
                "code": "30981-5",
                "display": "Earliest date to give"
              }
            ]
          },
          "value": "2025-02-28"
        },
        {
          "code": {
            "coding": [
              {
                "system": "http://loinc.org/",
                "code": "30980-7",
                "display": "Date vaccine due"
              }
            ]
          },
          "value": "2025-03-10"
        },
        {
          "code": {
            "coding": [
              {
                "system": "http://loinc.org/",
                "code": "59778-1",
                "display": "Date when overdue for immunization"
              }
            ]
          },
          "value": "2025-04-10"
        }
      ],
      "doseNumberString": "3",
      "seriesDosesString": "5",
      "supportingImmunization": [
        {
          "reference": "Immunization/3"
        }
      ]
    },
    {
      "vaccineCode": [
        {
          "coding": [
            {
              "system": "http://hl7.org/fhir/sid/cvx",
              "code": "20",
              "display": "diphtheria, tetanus toxoids and acellular pertussis vaccine"
            }
          ],
          "text": "DTaP"
        }
      ],
      "dateCriterion": [
        {
          "code": {
            "coding": [
              {
                "system": "http://loinc.org/",
                "code": "30981-5",
                "display": "Earliest date to give"
              }
            ]
          },
          "value": "2025-02-28"
        },
        {
          "code": {
            "coding": [
              {
                "system": "http://loinc.org/",
                "code": "30980-7",
                "display": "Date vaccine due"
              }
            ]
          },
          "value": "2025-03-10"
        },
        {
          "code": {
            "coding": [
              {
                "system": "http://loinc.org/",
                "code": "59778-1",
                "display": "Date when overdue for immunization"
              }
            ]
          },
          "value": "2025-04-10"
        }
      ],
      "doseNumberString": "4",
      "seriesDosesString": "5",
      "supportingImmunization": [
        {
          "reference": "Immunization/3"
        }
      ]
    },
    {
      "vaccineCode": [
        {
          "coding": [
            {
              "system": "http://hl7.org/fhir/sid/cvx",
              "code": "20",
              "display": "diphtheria, tetanus toxoids and acellular pertussis vaccine"
            }
          ],
          "text": "DTaP"
        }
      ],
      "dateCriterion": [
        {
          "code": {
            "coding": [
              {
                "system": "http://loinc.org/",
                "code": "30981-5",
                "display": "Earliest date to give"
              }
            ]
          },
          "value": "2025-02-28"
        },
        {
          "code": {
            "coding": [
              {
                "system": "http://loinc.org/",
                "code": "30980-7",
                "display": "Date vaccine due"
              }
            ]
          },
          "value": "2025-03-10"
        },
        {
          "code": {
            "coding": [
              {
                "system": "http://loinc.org/",
                "code": "59778-1",
                "display": "Date when overdue for immunization"
              }
            ]
          },
          "value": "2025-04-10"
        }
      ],
      "doseNumberString": "5",
      "seriesDosesString": "5",
      "supportingImmunization": [
        {
          "reference": "Immunization/3"
        }
      ]
    }
  ]
}

```

## Haemophilus influenzae type b vaccine, conjugate unspecified formulation

```javascript
{
  "resourceType": "ImmunizationRecommendation",
  "id": "1",
  "patient": {
    "reference": "Patient/1"
  },
  "date": "2025-02-25",
  "authority": {
    "reference": "Organization/2",
    
  },
  "recommendation": [
    {
      "vaccineCode": [
        {
          "coding": [
            {
              "system": "http://hl7.org/fhir/sid/cvx",
              "code": "17",
              "display": "Haemophilus influenzae type b vaccine, conjugate unspecified formulation"
            }
          ],
          "text": "Hib, unspecified formulation"
        }
      ],
      "dateCriterion": [
        {
          "code": {
            "coding": [
              {
                "system": "http://loinc.org/",
                "code": "30981-5",
                "display": "Earliest date to give"
              }
            ]
          },
          "value": "2025-02-28"
        },
        {
          "code": {
            "coding": [
              {
                "system": "http://loinc.org/",
                "code": "30980-7",
                "display": "Date vaccine due"
              }
            ]
          },
          "value": "2025-03-10"
        },
        {
          "code": {
            "coding": [
              {
                "system": "http://loinc.org/",
                "code": "59778-1",
                "display": "Date when overdue for immunization"
              }
            ]
          },
          "value": "2025-04-10"
        }
      ],
      "doseNumberString": "1",
      "seriesDosesString": "4",
      "supportingImmunization": [
        {
          "reference": "Immunization/3"
        }
      ]
    },
    {
      "vaccineCode": [
        {
          "coding": [
            {
              "system": "http://hl7.org/fhir/sid/cvx",
              "code": "17",
              "display": "Haemophilus influenzae type b vaccine, conjugate unspecified formulation"
            }
          ],
          "text": "Hib, unspecified formulation"
        }
      ],
      "dateCriterion": [
        {
          "code": {
            "coding": [
              {
                "system": "http://loinc.org/",
                "code": "30981-5",
                "display": "Earliest date to give"
              }
            ]
          },
          "value": "2025-02-28"
        },
        {
          "code": {
            "coding": [
              {
                "system": "http://loinc.org/",
                "code": "30980-7",
                "display": "Date vaccine due"
              }
            ]
          },
          "value": "2025-03-10"
        },
        {
          "code": {
            "coding": [
              {
                "system": "http://loinc.org/",
                "code": "59778-1",
                "display": "Date when overdue for immunization"
              }
            ]
          },
          "value": "2025-04-10"
        }
      ],
      "doseNumberString": "2",
      "seriesDosesString": "4",
      "supportingImmunization": [
        {
          "reference": "Immunization/3"
        }
      ]
    },
    {
      "vaccineCode": [
        {
          "coding": [
            {
              "system": "http://hl7.org/fhir/sid/cvx",
              "code": "17",
              "display": "Haemophilus influenzae type b vaccine, conjugate unspecified formulation"
            }
          ],
          "text": "Hib, unspecified formulation"
        }
      ],
      "dateCriterion": [
        {
          "code": {
            "coding": [
              {
                "system": "http://loinc.org/",
                "code": "30981-5",
                "display": "Earliest date to give"
              }
            ]
          },
          "value": "2025-02-28"
        },
        {
          "code": {
            "coding": [
              {
                "system": "http://loinc.org/",
                "code": "30980-7",
                "display": "Date vaccine due"
              }
            ]
          },
          "value": "2025-03-10"
        },
        {
          "code": {
            "coding": [
              {
                "system": "http://loinc.org/",
                "code": "59778-1",
                "display": "Date when overdue for immunization"
              }
            ]
          },
          "value": "2025-04-10"
        }
      ],
      "doseNumberString": "3",
      "seriesDosesString": "4",
      "supportingImmunization": [
        {
          "reference": "Immunization/3"
        }
      ]
    },
    {
      "vaccineCode": [
        {
          "coding": [
            {
              "system": "http://hl7.org/fhir/sid/cvx",
              "code": "17",
              "display": "Haemophilus influenzae type b vaccine, conjugate unspecified formulation"
            }
          ],
          "text": "Hib, unspecified formulation"
        }
      ],
      "dateCriterion": [
        {
          "code": {
            "coding": [
              {
                "system": "http://loinc.org/",
                "code": "30981-5",
                "display": "Earliest date to give"
              }
            ]
          },
          "value": "2025-02-28"
        },
        {
          "code": {
            "coding": [
              {
                "system": "http://loinc.org/",
                "code": "30980-7",
                "display": "Date vaccine due"
              }
            ]
          },
          "value": "2025-03-10"
        },
        {
          "code": {
            "coding": [
              {
                "system": "http://loinc.org/",
                "code": "59778-1",
                "display": "Date when overdue for immunization"
              }
            ]
          },
          "value": "2025-04-10"
        }
      ],
      "doseNumberString": "4",
      "seriesDosesString": "4",
      "supportingImmunization": [
        {
          "reference": "Immunization/3"
        }
      ]
    }
  ]
}

```

## pneumococcal conjugate vaccine, 13 valent

```javascript
{
  "resourceType": "ImmunizationRecommendation",
  "id": "1",
  "patient": {
    "reference": "Patient/1"
  },
  "date": "2025-02-25",
  "authority": {
    "reference": "Organization/2",
    
  },
  "recommendation": [
    {
      "vaccineCode": [
        {
          "coding": [
            {
              "system": "http://hl7.org/fhir/sid/cvx",
              "code": "133",
              "display": "pneumococcal conjugate vaccine, 13 valent"
            }
          ],
          "text": "Pneumococcal conjugate PCV 13"
        }
      ],
      "dateCriterion": [
        {
          "code": {
            "coding": [
              {
                "system": "http://loinc.org/",
                "code": "30981-5",
                "display": "Earliest date to give"
              }
            ]
          },
          "value": "2025-02-28"
        },
        {
          "code": {
            "coding": [
              {
                "system": "http://loinc.org/",
                "code": "30980-7",
                "display": "Date vaccine due"
              }
            ]
          },
          "value": "2025-03-10"
        },
        {
          "code": {
            "coding": [
              {
                "system": "http://loinc.org/",
                "code": "59778-1",
                "display": "Date when overdue for immunization"
              }
            ]
          },
          "value": "2025-04-10"
        }
      ],
      "doseNumberString": "1",
      "seriesDosesString": "4",
      "supportingImmunization": [
        {
          "reference": "Immunization/3"
        }
      ]
    },
    {
      "vaccineCode": [
        {
          "coding": [
            {
              "system": "http://hl7.org/fhir/sid/cvx",
              "code": "133",
              "display": "pneumococcal conjugate vaccine, 13 valent"
            }
          ],
          "text": "Pneumococcal conjugate PCV 13"
        }
      ],
      "dateCriterion": [
        {
          "code": {
            "coding": [
              {
                "system": "http://loinc.org/",
                "code": "30981-5",
                "display": "Earliest date to give"
              }
            ]
          },
          "value": "2025-02-28"
        },
        {
          "code": {
            "coding": [
              {
                "system": "http://loinc.org/",
                "code": "30980-7",
                "display": "Date vaccine due"
              }
            ]
          },
          "value": "2025-03-10"
        },
        {
          "code": {
            "coding": [
              {
                "system": "http://loinc.org/",
                "code": "59778-1",
                "display": "Date when overdue for immunization"
              }
            ]
          },
          "value": "2025-04-10"
        }
      ],
      "doseNumberString": "2",
      "seriesDosesString": "4",
      "supportingImmunization": [
        {
          "reference": "Immunization/3"
        }
      ]
    },
    {
      "vaccineCode": [
        {
          "coding": [
            {
              "system": "http://hl7.org/fhir/sid/cvx",
              "code": "133",
              "display": "pneumococcal conjugate vaccine, 13 valent"
            }
          ],
          "text": "Pneumococcal conjugate PCV 13"
        }
      ],
      "dateCriterion": [
        {
          "code": {
            "coding": [
              {
                "system": "http://loinc.org/",
                "code": "30981-5",
                "display": "Earliest date to give"
              }
            ]
          },
          "value": "2025-02-28"
        },
        {
          "code": {
            "coding": [
              {
                "system": "http://loinc.org/",
                "code": "30980-7",
                "display": "Date vaccine due"
              }
            ]
          },
          "value": "2025-03-10"
        },
        {
          "code": {
            "coding": [
              {
                "system": "http://loinc.org/",
                "code": "59778-1",
                "display": "Date when overdue for immunization"
              }
            ]
          },
          "value": "2025-04-10"
        }
      ],
      "doseNumberString": "3",
      "seriesDosesString": "4",
      "supportingImmunization": [
        {
          "reference": "Immunization/3"
        }
      ]
    },
    {
      "vaccineCode": [
        {
          "coding": [
            {
              "system": "http://hl7.org/fhir/sid/cvx",
              "code": "133",
              "display": "pneumococcal conjugate vaccine, 13 valent"
            }
          ],
          "text": "Pneumococcal conjugate PCV 13"
        }
      ],
      "dateCriterion": [
        {
          "code": {
            "coding": [
              {
                "system": "http://loinc.org/",
                "code": "30981-5",
                "display": "Earliest date to give"
              }
            ]
          },
          "value": "2025-02-28"
        },
        {
          "code": {
            "coding": [
              {
                "system": "http://loinc.org/",
                "code": "30980-7",
                "display": "Date vaccine due"
              }
            ]
          },
          "value": "2025-03-10"
        },
        {
          "code": {
            "coding": [
              {
                "system": "http://loinc.org/",
                "code": "59778-1",
                "display": "Date when overdue for immunization"
              }
            ]
          },
          "value": "2025-04-10"
        }
      ],
      "doseNumberString": "4",
      "seriesDosesString": "4",
      "supportingImmunization": [
        {
          "reference": "Immunization/3"
        }
      ]
    }
  ]
}

```

## rotavirus, live, pentavalent vaccine

```javascript
{
  "resourceType": "ImmunizationRecommendation",
  "id": "1",
  "patient": {
    "reference": "Patient/1"
  },
  "date": "2025-02-25",
  "authority": {
    "reference": "Organization/2",
    
  },
  "recommendation": [
    {
      "vaccineCode": [
        {
          "coding": [
            {
              "system": "http://hl7.org/fhir/sid/cvx",
              "code": "122",
              "display": "rotavirus, live, pentavalent vaccine"
            }
          ],
          "text": "rotavirus, pentavalent"
        }
      ],
      "dateCriterion": [
        {
          "code": {
            "coding": [
              {
                "system": "http://loinc.org/",
                "code": "30981-5",
                "display": "Earliest date to give"
              }
            ]
          },
          "value": "2025-02-28"
        },
        {
          "code": {
            "coding": [
              {
                "system": "http://loinc.org/",
                "code": "30980-7",
                "display": "Date vaccine due"
              }
            ]
          },
          "value": "2025-03-10"
        },
        {
          "code": {
            "coding": [
              {
                "system": "http://loinc.org/",
                "code": "59778-1",
                "display": "Date when overdue for immunization"
              }
            ]
          },
          "value": "2025-04-10"
        }
      ],
      "doseNumberString": "1",
      "seriesDosesString": "3",
      "supportingImmunization": [
        {
          "reference": "Immunization/3"
        }
      ]
    },
    {
      "vaccineCode": [
        {
          "coding": [
            {
              "system": "http://hl7.org/fhir/sid/cvx",
              "code": "122",
              "display": "rotavirus, live, pentavalent vaccine"
            }
          ],
          "text": "rotavirus, pentavalent"
        }
      ],
      "dateCriterion": [
        {
          "code": {
            "coding": [
              {
                "system": "http://loinc.org/",
                "code": "30981-5",
                "display": "Earliest date to give"
              }
            ]
          },
          "value": "2025-02-28"
        },
        {
          "code": {
            "coding": [
              {
                "system": "http://loinc.org/",
                "code": "30980-7",
                "display": "Date vaccine due"
              }
            ]
          },
          "value": "2025-03-10"
        },
        {
          "code": {
            "coding": [
              {
                "system": "http://loinc.org/",
                "code": "59778-1",
                "display": "Date when overdue for immunization"
              }
            ]
          },
          "value": "2025-04-10"
        }
      ],
      "doseNumberString": "2",
      "seriesDosesString": "3",
      "supportingImmunization": [
        {
          "reference": "Immunization/3"
        }
      ]
    },
    {
      "vaccineCode": [
        {
          "coding": [
            {
              "system": "http://hl7.org/fhir/sid/cvx",
              "code": "122",
              "display": "rotavirus, live, pentavalent vaccine"
            }
          ],
          "text": "rotavirus, pentavalent"
        }
      ],
      "dateCriterion": [
        {
          "code": {
            "coding": [
              {
                "system": "http://loinc.org/",
                "code": "30981-5",
                "display": "Earliest date to give"
              }
            ]
          },
          "value": "2025-02-28"
        },
        {
          "code": {
            "coding": [
              {
                "system": "http://loinc.org/",
                "code": "30980-7",
                "display": "Date vaccine due"
              }
            ]
          },
          "value": "2025-03-10"
        },
        {
          "code": {
            "coding": [
              {
                "system": "http://loinc.org/",
                "code": "59778-1",
                "display": "Date when overdue for immunization"
              }
            ]
          },
          "value": "2025-04-10"
        }
      ],
      "doseNumberString": "3",
      "seriesDosesString": "3",
      "supportingImmunization": [
        {
          "reference": "Immunization/3"
        }
      ]
    }
  ]
}

```

## influenza virus vaccine, whole virus

```javascript
{
  "resourceType": "ImmunizationRecommendation",
  "id": "1",
  "patient": {
    "reference": "Patient/1"
  },
  "date": "2025-02-25",
  "authority": {
    "reference": "Organization/2",
    
  },
  "recommendation": [
    {
      "vaccineCode": [
        {
          "coding": [
            {
              "system": "http://hl7.org/fhir/sid/cvx",
              "code": "88",
              "display": "influenza virus vaccine, whole virus"
            }
          ],
          "text": "influenza, whole"
        }
      ],
      "dateCriterion": [
        {
          "code": {
            "coding": [
              {
                "system": "http://loinc.org/",
                "code": "30981-5",
                "display": "Earliest date to give"
              }
            ]
          },
          "value": "2025-02-28"
        },
        {
          "code": {
            "coding": [
              {
                "system": "http://loinc.org/",
                "code": "30980-7",
                "display": "Date vaccine due"
              }
            ]
          },
          "value": "2025-03-10"
        },
        {
          "code": {
            "coding": [
              {
                "system": "http://loinc.org/",
                "code": "59778-1",
                "display": "Date when overdue for immunization"
              }
            ]
          },
          "value": "2025-04-10"
        }
      ],
      "doseNumberString": "1",
      "seriesDosesString": "2",
      "supportingImmunization": [
        {
          "reference": "Immunization/3"
        }
      ]
    },
    {
      "vaccineCode": [
        {
          "coding": [
            {
              "system": "http://hl7.org/fhir/sid/cvx",
              "code": "88",
              "display": "influenza virus vaccine, whole virus"
            }
          ],
          "text": "influenza, whole"
        }
      ],
      "dateCriterion": [
        {
          "code": {
            "coding": [
              {
                "system": "http://loinc.org/",
                "code": "30981-5",
                "display": "Earliest date to give"
              }
            ]
          },
          "value": "2025-02-28"
        },
        {
          "code": {
            "coding": [
              {
                "system": "http://loinc.org/",
                "code": "30980-7",
                "display": "Date vaccine due"
              }
            ]
          },
          "value": "2025-03-10"
        },
        {
          "code": {
            "coding": [
              {
                "system": "http://loinc.org/",
                "code": "59778-1",
                "display": "Date when overdue for immunization"
              }
            ]
          },
          "value": "2025-04-10"
        }
      ],
      "doseNumberString": "2",
      "seriesDosesString": "2",
      "supportingImmunization": [
        {
          "reference": "Immunization/3"
        }
      ]
    }
  ]
}

```

## measles, mumps and rubella virus vaccine

```javascript
{
  "resourceType": "ImmunizationRecommendation",
  "id": "1",
  "patient": {
    "reference": "Patient/1"
  },
  "date": "2025-02-25",
  "authority": {
    "reference": "Organization/2",
    
  },
  "recommendation": [
    {
      "vaccineCode": [
        {
          "coding": [
            {
              "system": "http://hl7.org/fhir/sid/cvx",
              "code": "3",
              "display": "measles, mumps and rubella virus vaccine"
            }
          ],
          "text": "MMR"
        }
      ],
      "dateCriterion": [
        {
          "code": {
            "coding": [
              {
                "system": "http://loinc.org/",
                "code": "30981-5",
                "display": "Earliest date to give"
              }
            ]
          },
          "value": "2025-02-28"
        },
        {
          "code": {
            "coding": [
              {
                "system": "http://loinc.org/",
                "code": "30980-7",
                "display": "Date vaccine due"
              }
            ]
          },
          "value": "2025-03-10"
        },
        {
          "code": {
            "coding": [
              {
                "system": "http://loinc.org/",
                "code": "59778-1",
                "display": "Date when overdue for immunization"
              }
            ]
          },
          "value": "2025-04-10"
        }
      ],
      "doseNumberString": "1",
      "seriesDosesString": "3",
      "supportingImmunization": [
        {
          "reference": "Immunization/3"
        }
      ]
    },
    {
      "vaccineCode": [
        {
          "coding": [
            {
              "system": "http://hl7.org/fhir/sid/cvx",
              "code": "3",
              "display": "measles, mumps and rubella virus vaccine"
            }
          ],
          "text": "MMR"
        }
      ],
      "dateCriterion": [
        {
          "code": {
            "coding": [
              {
                "system": "http://loinc.org/",
                "code": "30981-5",
                "display": "Earliest date to give"
              }
            ]
          },
          "value": "2025-02-28"
        },
        {
          "code": {
            "coding": [
              {
                "system": "http://loinc.org/",
                "code": "30980-7",
                "display": "Date vaccine due"
              }
            ]
          },
          "value": "2025-03-10"
        },
        {
          "code": {
            "coding": [
              {
                "system": "http://loinc.org/",
                "code": "59778-1",
                "display": "Date when overdue for immunization"
              }
            ]
          },
          "value": "2025-04-10"
        }
      ],
      "doseNumberString": "2",
      "seriesDosesString": "3",
      "supportingImmunization": [
        {
          "reference": "Immunization/3"
        }
      ]
    },
    {
      "vaccineCode": [
        {
          "coding": [
            {
              "system": "http://hl7.org/fhir/sid/cvx",
              "code": "3",
              "display": "measles, mumps and rubella virus vaccine"
            }
          ],
          "text": "MMR"
        }
      ],
      "dateCriterion": [
        {
          "code": {
            "coding": [
              {
                "system": "http://loinc.org/",
                "code": "30981-5",
                "display": "Earliest date to give"
              }
            ]
          },
          "value": "2025-02-28"
        },
        {
          "code": {
            "coding": [
              {
                "system": "http://loinc.org/",
                "code": "30980-7",
                "display": "Date vaccine due"
              }
            ]
          },
          "value": "2025-03-10"
        },
        {
          "code": {
            "coding": [
              {
                "system": "http://loinc.org/",
                "code": "59778-1",
                "display": "Date when overdue for immunization"
              }
            ]
          },
          "value": "2025-04-10"
        }
      ],
      "doseNumberString": "3",
      "seriesDosesString": "3",
      "supportingImmunization": [
        {
          "reference": "Immunization/3"
        }
      ]
    }
  ]
}

```

## Typhoid conjugate vaccine (non-US)

```javascript
{
  "resourceType": "ImmunizationRecommendation",
  "id": "1",
  "patient": {
    "reference": "Patient/1"
  },
  "date": "2025-02-25",
  "authority": {
    "reference": "Organization/2",
    
  },
  "recommendation": [
    {
      "vaccineCode": [
        {
          "coding": [
            {
              "system": "http://hl7.org/fhir/sid/cvx",
              "code": "190",
              "display": "Typhoid conjugate vaccine (non-US)"
            }
          ],
          "text": "Typhoid conjugate vaccine (TCV)"
        }
      ],
      "dateCriterion": [
        {
          "code": {
            "coding": [
              {
                "system": "http://loinc.org/",
                "code": "30981-5",
                "display": "Earliest date to give"
              }
            ]
          },
          "value": "2025-02-28"
        },
        {
          "code": {
            "coding": [
              {
                "system": "http://loinc.org/",
                "code": "30980-7",
                "display": "Date vaccine due"
              }
            ]
          },
          "value": "2025-03-10"
        },
        {
          "code": {
            "coding": [
              {
                "system": "http://loinc.org/",
                "code": "59778-1",
                "display": "Date when overdue for immunization"
              }
            ]
          },
          "value": "2025-04-10"
        }
      ],
      "doseNumberString": "1",
      "seriesDosesString": "1",
      "supportingImmunization": [
        {
          "reference": "Immunization/3"
        }
      ]
    }
  ]
}

```

## hepatitis A vaccine, pediatric/adolescent dosage, 3 dose schedule

```javascript
{
  "resourceType": "ImmunizationRecommendation",
  "id": "1",
  "patient": {
    "reference": "Patient/1"
  },
  "date": "2025-02-25",
  "authority": {
    "reference": "Organization/2",
    
  },
  "recommendation": [
    {
      "vaccineCode": [
        {
          "coding": [
            {
              "system": "http://hl7.org/fhir/sid/cvx",
              "code": "84",
              "display": "hepatitis A vaccine, pediatric/adolescent dosage, 3 dose schedule"
            }
          ],
          "text": "Hep A, ped/adol, 3 dose"
        }
      ],
      "dateCriterion": [
        {
          "code": {
            "coding": [
              {
                "system": "http://loinc.org/",
                "code": "30981-5",
                "display": "Earliest date to give"
              }
            ]
          },
          "value": "2025-02-28"
        },
        {
          "code": {
            "coding": [
              {
                "system": "http://loinc.org/",
                "code": "30980-7",
                "display": "Date vaccine due"
              }
            ]
          },
          "value": "2025-03-10"
        },
        {
          "code": {
            "coding": [
              {
                "system": "http://loinc.org/",
                "code": "59778-1",
                "display": "Date when overdue for immunization"
              }
            ]
          },
          "value": "2025-04-10"
        }
      ],
      "doseNumberString": "1",
      "seriesDosesString": "2",
      "supportingImmunization": [
        {
          "reference": "Immunization/3"
        }
      ]
    },
    {
      "vaccineCode": [
        {
          "coding": [
            {
              "system": "http://hl7.org/fhir/sid/cvx",
              "code": "84",
              "display": "hepatitis A vaccine, pediatric/adolescent dosage, 3 dose schedule"
            }
          ],
          "text": "Hep A, ped/adol, 3 dose"
        }
      ],
      "dateCriterion": [
        {
          "code": {
            "coding": [
              {
                "system": "http://loinc.org/",
                "code": "30981-5",
                "display": "Earliest date to give"
              }
            ]
          },
          "value": "2025-02-28"
        },
        {
          "code": {
            "coding": [
              {
                "system": "http://loinc.org/",
                "code": "30980-7",
                "display": "Date vaccine due"
              }
            ]
          },
          "value": "2025-03-10"
        },
        {
          "code": {
            "coding": [
              {
                "system": "http://loinc.org/",
                "code": "59778-1",
                "display": "Date when overdue for immunization"
              }
            ]
          },
          "value": "2025-04-10"
        }
      ],
      "doseNumberString": "2",
      "seriesDosesString": "2",
      "supportingImmunization": [
        {
          "reference": "Immunization/3"
        }
      ]
    }
  ]
}

```

## varicella virus vaccine
```javascript
{
  "resourceType": "ImmunizationRecommendation",
  "id": "1",
  "patient": {
    "reference": "Patient/1"
  },
  "date": "2025-02-25",
  "authority": {
    "reference": "Organization/2",
    
  },
  "recommendation": [
    {
      "vaccineCode": [
        {
          "coding": [
            {
              "system": "http://hl7.org/fhir/sid/cvx",
              "code": "21",
              "display": "varicella virus vaccine"
            }
          ],
          "text": "varicella"
        }
      ],
      "dateCriterion": [
        {
          "code": {
            "coding": [
              {
                "system": "http://loinc.org/",
                "code": "30981-5",
                "display": "Earliest date to give"
              }
            ]
          },
          "value": "2025-02-28"
        },
        {
          "code": {
            "coding": [
              {
                "system": "http://loinc.org/",
                "code": "30980-7",
                "display": "Date vaccine due"
              }
            ]
          },
          "value": "2025-03-10"
        },
        {
          "code": {
            "coding": [
              {
                "system": "http://loinc.org/",
                "code": "59778-1",
                "display": "Date when overdue for immunization"
              }
            ]
          },
          "value": "2025-04-10"
        }
      ],
      "doseNumberString": "1",
      "seriesDosesString": "2",
      "supportingImmunization": [
        {
          "reference": "Immunization/3"
        }
      ]
    },
    {
      "vaccineCode": [
        {
          "coding": [
            {
              "system": "http://hl7.org/fhir/sid/cvx",
              "code": "21",
              "display": "varicella virus vaccine"
            }
          ],
          "text": "varicella"
        }
      ],
      "dateCriterion": [
        {
          "code": {
            "coding": [
              {
                "system": "http://loinc.org/",
                "code": "30981-5",
                "display": "Earliest date to give"
              }
            ]
          },
          "value": "2025-02-28"
        },
        {
          "code": {
            "coding": [
              {
                "system": "http://loinc.org/",
                "code": "30980-7",
                "display": "Date vaccine due"
              }
            ]
          },
          "value": "2025-03-10"
        },
        {
          "code": {
            "coding": [
              {
                "system": "http://loinc.org/",
                "code": "59778-1",
                "display": "Date when overdue for immunization"
              }
            ]
          },
          "value": "2025-04-10"
        }
      ],
      "doseNumberString": "2",
      "seriesDosesString": "2",
      "supportingImmunization": [
        {
          "reference": "Immunization/3"
        }
      ]
    }
  ]
}

```

## tetanus toxoid, reduced diphtheria toxoid, and acellular pertussis vaccine, adsorbed

```javascript
{
  "resourceType": "ImmunizationRecommendation",
  "id": "1",
  "patient": {
    "reference": "Patient/1"
  },
  "date": "2025-02-25",
  "authority": {
    "reference": "Organization/2",
    
  },
  "recommendation": [
    {
      "vaccineCode": [
        {
          "coding": [
            {
              "system": "http://hl7.org/fhir/sid/cvx",
              "code": "115",
              "display": "tetanus toxoid, reduced diphtheria toxoid, and acellular pertussis vaccine, adsorbed"
            }
          ],
          "text": "Tdap"
        }
      ],
      "dateCriterion": [
        {
          "code": {
            "coding": [
              {
                "system": "http://loinc.org/",
                "code": "30981-5",
                "display": "Earliest date to give"
              }
            ]
          },
          "value": "2025-02-28"
        },
        {
          "code": {
            "coding": [
              {
                "system": "http://loinc.org/",
                "code": "30980-7",
                "display": "Date vaccine due"
              }
            ]
          },
          "value": "2025-03-10"
        },
        {
          "code": {
            "coding": [
              {
                "system": "http://loinc.org/",
                "code": "59778-1",
                "display": "Date when overdue for immunization"
              }
            ]
          },
          "value": "2025-04-10"
        }
      ],
      "doseNumberString": "1",
      "seriesDosesString": "1",
      "supportingImmunization": [
        {
          "reference": "Immunization/3"
        }
      ]
    }
  ]
}

```

## human papilloma virus vaccine, quadrivalent

```javascript
{
  "resourceType": "ImmunizationRecommendation",
  "id": "1",
  "patient": {
    "reference": "Patient/1"
  },
  "date": "2025-02-25",
  "authority": {
    "reference": "Organization/2",
    
  },
  "recommendation": [
    {
      "vaccineCode": [
        {
          "coding": [
            {
              "system": "http://hl7.org/fhir/sid/cvx",
              "code": "62",
              "display": "human papilloma virus vaccine, quadrivalent"
            }
          ],
          "text": "HPV, quadrivalent"
        }
      ],
      "dateCriterion": [
        {
          "code": {
            "coding": [
              {
                "system": "http://loinc.org/",
                "code": "30981-5",
                "display": "Earliest date to give"
              }
            ]
          },
          "value": "2025-02-28"
        },
        {
          "code": {
            "coding": [
              {
                "system": "http://loinc.org/",
                "code": "30980-7",
                "display": "Date vaccine due"
              }
            ]
          },
          "value": "2025-03-10"
        },
        {
          "code": {
            "coding": [
              {
                "system": "http://loinc.org/",
                "code": "59778-1",
                "display": "Date when overdue for immunization"
              }
            ]
          },
          "value": "2025-04-10"
        }
      ],
      "doseNumberString": "1",
      "seriesDosesString": "2",
      "supportingImmunization": [
        {
          "reference": "Immunization/3"
        }
      ]
    },
    {
      "vaccineCode": [
        {
          "coding": [
            {
              "system": "http://hl7.org/fhir/sid/cvx",
              "code": "62",
              "display": "human papilloma virus vaccine, quadrivalent"
            }
          ],
          "text": "HPV, quadrivalent"
        }
      ],
      "dateCriterion": [
        {
          "code": {
            "coding": [
              {
                "system": "http://loinc.org/",
                "code": "30981-5",
                "display": "Earliest date to give"
              }
            ]
          },
          "value": "2025-02-28"
        },
        {
          "code": {
            "coding": [
              {
                "system": "http://loinc.org/",
                "code": "30980-7",
                "display": "Date vaccine due"
              }
            ]
          },
          "value": "2025-03-10"
        },
        {
          "code": {
            "coding": [
              {
                "system": "http://loinc.org/",
                "code": "59778-1",
                "display": "Date when overdue for immunization"
              }
            ]
          },
          "value": "2025-04-10"
        }
      ],
      "doseNumberString": "2",
      "seriesDosesString": "2",
      "supportingImmunization": [
        {
          "reference": "Immunization/3"
        }
      ]
    }
  ]
}

```
