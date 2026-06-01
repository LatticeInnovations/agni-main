## Create Vitals : 
> Endpoint : POST {{URL}}/v1/sync/Observation

> [!NOTE]  
> Appointment must be created at front-end before creating vitals. As it will create encounter also, which we required to link in all the Observation resources. This must be handled at front-end. Also there must exist only one appointment and encounter for a given day for a patient/student.

- https://docs.google.com/document/d/1tea1vF-fFNjooZUyRevXdJbL7an9FpN_W_IMKyF-xYE/edit?usp=drive_web

#### Request Body : 
- While creating a vital for a patient, client-end must send all the field in request body to backend.
- If height is entered in `cm`, then `heightFt` and `heightInch` must be empty string or null and `heightCm` must contain the value.
- If height is entered in `ft` and `inch`, then `heightCm` must be empty string or null and both `heightFt` and `heightInch` must contain the value.
- `tempUnit` must contain only `C` or `F` as values.
- `bloodGlucoseType` must contain only `fasting` or `random` as values.
- `bloodGlucoseUnit` must contain only `mg/dL` or `mmol/L` as values.
- `eyeTestType` must contain only `1` or `2` as values for `with glasses` and `without glasses`.
- `leftEye` and `rightEye` can have values from `1` to `7`. These number are mapped to the options for left and right eye. Ex: `1` means `Normal Vision (6/6 or 20/20)`. This mapping must be done at client-end.
- `cholesterol` and `cholesterolUnit` both values must be present if user is saving cholesterol value.
```
[
  {
    "vitalUuid": "e4719ac7-9b1f-42e2-9071-cd918e637cf9", // vital uuid created at android end
    "appointmentId": "44", // send the appointment id of created appointment resource
    "patientId": "7", // patient id
    "heightFt": "",
    "heightInch": "",
    "heightCm": "175",
    "weight": "65",
    "heartRate": "80",
    "respRate": "66",
    "spo2": "89",
    "temp": "45",
    "tempUnit": "F", //C or F only
    "bpDiastolic": "130",
    "bpSystolic": "97",
    "bloodGlucose": "66",
    "bloodGlucoseType": "random", // fasting or random only
    "bloodGlucoseUnit": "mmol/L", //mg/dL or mmol/L only 
    "leftEye": "2",
    "rightEye": "3",
    "eyeTestType": "2", // 1 or 2 only
    "cholesterol": 4,
    "cholesterolUnit": "mg/dl",
    "createdOn": "2024-10-09" // must be the timestamp when the vital is created
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
      "id": "92ec7af7-3bfa-473c-ad7f-a1b1002eb7a8",
      "err": null,
      "fhirId": "46" // this fhir ID will be used in patch request as vitalFhirId
    }
  ]
}
```


## Get Vitals 
> Endpoint : GET  {{URL}}/v1/Observation
- Client-side must fetch all the vitals together. 

#### Response body
```
{
  "status": 1,
  "message": "Data fetched",
  "total": 2,
  "data": [
    {
      "appointmentUuid": "1324asfdf-sfaasdfaf-asd-bjadsfgafoiwqoi-iuweqsnf",
      "vitalFhirId": "32", // this is encounter id
      "appointmentId": "31",
      "practitionerName": "Himanshu",
      "patientId": "5",
      "heightFt": null,
      "heightInch": null,
      "heightCm": 50,
      "weight": 50,
      "heartRate": 50,
      "respRate": 50,
      "spo2": 50,
      "temp": 50,
      "tempUnit": "C",
      "bpDiastolic": 50,
      "bpSystolic": 50,
      "bloodGlucoseType": "fasting",
      "bloodGlucose": 50,
      "bloodGlucoseUnit": "mg/dL",
      "eyeTestType": "2",
      "leftEye": 1,
      "rightEye": 2,
      "cholesterol": 4,
      "cholesterolUnit": "mg/dl"
    },
    {
      "appointmentUuid": "1231432asfdf-sfaasdfaf-asd-bjadzvcoiwqoi-iuweqsnf",
      "vitalFhirId": "32",
      "practitionerName": "Himanshu",
      "appointmentId": "44",
      "patientId": "7",
      "heightFt": null,
      "heightInch": null,
      "heightCm": 175,
      "weight": 65,
      "heartRate": 80,
      "respRate": 26,
      "spo2": 89,
      "temp": 45,
      "tempUnit": "F",
      "bpDiastolic": 130,
      "bpSystolic": 97,
      "bloodGlucoseType": "random",
      "bloodGlucose": 66,
      "bloodGlucoseUnit": "mmol/L",
      "eyeTestType": "2",
      "leftEye": 2,
      "rightEye": 3,
      "cholesterol": 4,
      "cholesterolUnit": "mg/dl"
    }
  ]
}
```
