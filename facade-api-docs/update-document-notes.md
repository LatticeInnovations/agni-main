## Description : 
- Document Notes can be updated whether it is document uploaded in prescription, medical report or lab report.

## Update Notes : 
> PATCH : {{URL}}/v1/sync/DocumentReference

#### Request Body : 
- send the notes as string, if notes are removed then send empty string.
- filename must be same as existing filename always.
- `documentFhirId` in request body is `documentFhirId` in case of prescription document.
- `documentFhirId` in request body is `labDocumentfhirId` in case of lab report.
- `documentFhirId` in request body is `medicalRecordFhirId` in case of medical report. 
  
```json
[
  {
    "documentFhirId": "765",
    "note": "",
    "filename": "3423432424545.jpeg"
  }
]
```

#### Response body : 
```json
{
  "status": 1,
  "message": "Data updated successfully.",
  "data": [
    {
      "status": "200 OK",
      "id": null,
      "err": null,
      "fhirId": "765"
    }
  ]
}
```
