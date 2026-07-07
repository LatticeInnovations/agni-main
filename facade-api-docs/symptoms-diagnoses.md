
# Symptoms and diagnoses
This section describes the flow of symptoms and diagnoses section.

### Resources
1. **Encounter resource** 
- If condition resource does not exist create one else link to the existing encounter of the patient for current date.
- [Resource link](/fhir-resources/symptom-diagnosis-encounter.md)
2. **Condition resource**
- Create a [Condition](/fhir-resources/condition.md) resource for storing all the symptoms and their diagnosis as well

## Fetch the symptom list
!!!
GET `{url}/ValueSet?name=symptomsList`
!!!

Set query parameter `name` as `symptomsList` to fetch the entire list of symptoms.

```json Response body
{
  "status": 2,
  "message": "Data fetched successfully.",
  "total": 1,
  "offset": null,
  "data": [
    {
      "symptoms": [
        {
          "code": "Headache",
          "display": "Headache",
          "type": "Head",
          "gender": null
        },
        {
          "code": "Cramps before period",
          "display": "Cramps before period",
          "type": "Middle abdomen",
          "gender": "female"
        },
        {
          "code": "Intermittent urine flow",
          "display": "Intermittent urine flow",
          "type": "Sexual organs",
          "gender": "male"
        }
      ]
    }
  ]
}
```


## Fetch the Diagnosis list
!!!
GET `{url}/ValueSet?name=diagnosisList`
!!!

Set query parameter `name` as `diagnosisList` to fetch all diagnoses.


```json Response body
{
  "status": 2,
  "message": "Data fetched successfully.",
  "total": 1,
  "offset": null,
  "data": [
    {
      "diagnosis": [
        {
          "code": "A000",
          "display": "Cholera due to Vibrio cholerae 01, biovar cholerae"
        },
        {
          "code": "A001",
          "display": "Cholera due to Vibrio cholerae 01, biovar eltor"
        },
        {
          "code": "A009",
          "display": "Cholera, unspecified"
        },
      ]
    }
  ]
}
```



## Create a symptom or a diagnosis
!!!
POST `{Url}/sync/Condition`
!!!

- `symptom` array in request body will contain the code fetched from ValueSet resource symptom mentioned in above query.
- `diagnosis` array in request body will contain the code fetched from ValueSet resource diagnosis mentioned in above query.
- `symDiagUuid` will be generated at frontend.

```json Request body
[
  {
    "appointmentId": 74, 
    "symDiagUuid": "e7a06cae-56bd-4afb-ba10-3a61ab94a307",
    "createdOn": "2024-10-14",
    "symptoms": [
      "R00",
      "R03"
    ],
    "diagnosis": [
      "A000",
      "A010"
    ]
  }
]
```

```json Response body
{
  "status": 1,
  "message": "Data saved successfully.",
  "data": [
    {
      "status": "201 Created",
      "id": "e7a06cae-56bd-4afb-ba10-3a61ab94a307",
      "err": null,
      "fhirId": "230"
    }
  ]
}
```


## Update a symptom or a diagnosis 
!!!
PATCH `{Url}/sync/Condition`
!!!
`symptoms` and `diagnosis` array will contain update symptom and diagnosis codes.

```json Request body
[
  {
    "symDiagFhirId": "230",
    "createdOn": "2024-10-15",
    "symptoms": [
      "R01"
    ],
    "diagnosis": [
      "A062"
    ]
  }
]
```

```json Response body
{
  "status": 1,
  "message": "Data updated successfully.",
  "data": [
    {
      "status": "200 OK",
      "id": null,
      "err": null,
      "fhirId": "230"
    }
  ]
}
```

## Fetch symptoms and diagnoses
!!!
GET `{Url}/Condition`
!!!

```json Response body
{
  "status": 1,
  "message": "Data fetched",
  "total": 2,
  "data": [
    {
      "appointmentUuid": "1233324fdf-sfaasdfaf-asd-bjadzvcoiwqoi-iuweqsnf",
      "appointmentId": "74",
      "symDiagFhirId": "229",
      "symptoms": [
        "R00",
        "R03"
      ],
      "diagnosis": [],
      "createdOn": "2024-10-14",
      "practitionerName": "Himanshu"
    },
    {
      "appointmentUuid": "1233324fdf-sfaasdfaf-asd-bjadzvcoiwqoi-iuweqsnf",
      "appointmentId": "75",
      "symDiagFhirId": "230",
      "symptoms": [
        "R00",
        "R03"
      ],
      "diagnosis": [
        "A000",
        "A010"
      ],
      "createdOn": "2024-10-14",
      "practitionerName": "Himanshu"
    }
  ]
}
```
