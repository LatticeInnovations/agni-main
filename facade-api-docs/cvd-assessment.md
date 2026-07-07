# CVD assessment

## Create CVD assessment
> Endpoint : POST /v1/sync/CVD

> [!NOTE]  
> The front-end must create an `Appointment` before creating a CVD assessment. Creating an `Appointment` creates an `Encounter`, to which all `Observation` resources are linked. Also, there must exist only one appointment and encounter on a given day for a patient.

- https://docs.google.com/document/d/1tea1vF-fFNjooZUyRevXdJbL7an9FpN_W_IMKyF-xYE/edit?usp=drive_web

#### Request Body : 
- While creating a CVD for a patient, client-end must send all the field in request body to backend.
- If height is entered in `cm`, then `heightFt` and `heightInch` must be empty string or null and `heightCm` must contain the value.
- If height is entered in `ft` and `inch`, then `heightCm` must be empty string or null and both `heightFt` and `heightInch` must contain the value.
  
```
[
  {
    "cvdUuid": "28576b8-a69f-414d-8877-8646ed338cca", // uuid generated at client end
    "appointmentId": "74", // appointment's FHIR id
    "patientId": "7", // patient's FHIR id
    "heightFt": 5, 
    "heightInch": 11,
    "heightCm": null,
    "weight": 53,
    "bpDiastolic": 117,
    "bpSystolic": 67,
    "diabetic": 1,  // 1 -> if diabetic, 0 -> if non diabetic
    "smoker": 1, // 1 -> if diabetic, 0 -> if non diabetic
    "cholesterol": 4,
    "cholesterolUnit": "mg/dl", // unit of cholesterol as a string
    "bmi": 25, // BMI value calculated at client end
    "risk": 4, // risk assessment score in percentage
    "createdOn": "2024-11-19" // date
  }
]
```

#### Response Body : 
- Fhir Ids of Observation resource is not required by front-end , so client side may or may not use this response.
```
{
  "status": 1,
  "message": "Data saved successfully.",
  "data": [
    {
      "status": "201 Created",
      "id": "28576b8-a69f-414d-8877-8646ed338cca",
      "err": null,
      "fhirId": "620"
    }
  ]
}
```

## Read CVD assessments
> Endpoint : GET  /v1/CVD 

```json Response body
{
  "status": 1,
  "message": "Data fetched",
  "total": 1,
  "data": [
    {
      "appointmentUuid": "28576b8-a69f-414d-8877-8646ed338cca",
      "appointmentId": "74",
      "patientId": "7",
      "generatedOn": "2024-11-19",
      "cvdUuid": "28576b8-a69f-414d-8877-8646ed338cca",
      "practitionerName": "Himanshu",
      "createdOn": "2024-11-19",
      "cvdFhirId": "620",
      "smoker": 1,
      "diabetic": 1,
      "heightFt": null,
      "heightInch": null,
      "heightCm": 50,
      "bmi": 100,
      "weight": 100,
      "bpDiastolic": 50,
      "bpSystolic": 50,
      "cholesterol": 500,
      "cholesterolUnit": "mmol/Dl",
      "risk": 5
    }
  ]
}
```

## Update CVD assessment
> Endpoint : PATCH /v1/sync/CVD

### Rules for the request body 
- `operation` can be `replace` or `add`. Replace if a value exists, and want to update it. Add if no value exists.
- The only exception is while updating diabetes and smoking status. Updates to these parameters always be via `add`.
- `key` must be exactly as mentioned in the example below.
- Only add the object which you want to patch.

```json Request body
[
  {
    "cvdFhirId": "620",
    "key": "Height",
    "component": {
      "operation": "replace",
      "heightFt": null,
      "heightInch": null,
      "heightCm": "50"
    }
  },
  {
    "cvdFhirId": "620",
    "key": "Weight",
    "component": {
      "operation": "replace",
      "weight": "100"
    }
  },
  {
    "cvdFhirId": "620",
    "key": "Diabetic status",
    "component": {
      "operation": "add",
      "diabetic": 1
    }
  },
  {
    "cvdFhirId": "620",
    "key": "Smoking Status",
    "component": {
      "operation": "add",
      "smoker": 1
    }
  },
  {
    "cvdFhirId": "620",
    "key": "Blood Pressure",
    "component": {
      "operation": "replace",
      "bpDiastolic": "50",
      "bpSystolic": "50"
    }
  },
  {
    "cvdFhirId": "620",
    "key": "Cholesterol",
    "component": {
      "operation": "replace",
      "cholesterol": 500,
      "cholesterolUnit": "mmol/Dl"
    }
  },
  {
    "cvdFhirId": "620",
    "key": "BMI",
    "component": {
      "operation": "replace",
      "bmi": 100
    }
  },
  {
    "cvdFhirId": "620",
    "key": "CVD Risk Percentage",
    "component": {
      "operation": "replace",
      "risk": 5
    }
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
      "fhirId": "621"
    },
    {
      "status": "200 OK",
      "id": null,
      "err": null,
      "fhirId": "622"
    },
    {
      "status": "200 OK",
      "id": null,
      "err": null,
      "fhirId": "623"
    },
    {
      "status": "200 OK",
      "id": null,
      "err": null,
      "fhirId": "624"
    },
    {
      "status": "200 OK",
      "id": null,
      "err": null,
      "fhirId": "625"
    },
    {
      "status": "200 OK",
      "id": null,
      "err": null,
      "fhirId": "626"
    },
    {
      "status": "200 OK",
      "id": null,
      "err": null,
      "fhirId": "627"
    },
    {
      "status": "200 OK",
      "id": null,
      "err": null,
      "fhirId": "628"
    }
  ]
}
```
