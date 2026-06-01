---
order: 500
---

## Create Lab Test : 
> Endpoint : POST {base url}/sync/DiagnosticReport


#### Request Body : 
- `diagnosticUuid` must be created at front-end to keep record of `DiagnosticReport` resource.
- Given below all the keys must be send in a request.
- `filename` must be a timestamp, changed at front-end. It will be used to show the date and time in view.
- `note` must be empty string or null, if a note is not added.
```json
[
  {
    "diagnosticUuid": "074fb161-1bca-4b72-99bc-b2e4058b38a2", // uuid created at front-end
    "appointmentId": "74", // appointment id
    "patientId": "7", // patient id
    "createdOn": "2024-12-03", 
    "files": [ 
      {
        "labDocumentUuid": "558430bc-d107-4aa4-a758-5b7a3c755a16", // uuid created at front-end
        "filename" : "1717669846000.jpg",
        "note": "lab report test 1"
      }
    ]
  }
]
```

#### Response Body : 
- `id` is the same uuid sent in request body as `diagnosticUuid`.
- `fhirId` is the id of new resource created. It is `diagnosticReportFhirId`.
- `labDocumentfhirId` is the id of new resource created.
- if the status of a lab report is `deleted`, it means it has been marked as deleted in respective resources and has to be removed from the client end during new sync. 
```json
{
  "status": 1,
  "message": "Data saved successfully.",
  "data": [
    {
      "status": "201 Created",
      "id": "074fb161-1bca-4b72-99bc-b2e4058b38a2",
      "files": [
        {
          "labDocumentfhirId": "844",
          "labDocumentUuid": "558430bc-d107-4aa4-a758-5b7a3c755a16"
        }
      ],
      "err": null,
      "fhirId": "843"
    }
  ]
}
```


## Get all Lab Test : 
> Endpoint : GET {base url}/DiagnosticReport

#### Response body : 

```json
{
  "status": 1,
  "message": "Data fetched",
  "total": 2,
  "data": [
    {
      "appointmentUuid": "1233324fdf-sfaasdfaf-asd-bjadzvcoiwqoi-iuweqsnf",
      "appointmentId": "74",
      "patientId": "7",
      "generatedOn": "2024-10-11",
      "diagnosticReport": [
         {
          "diagnosticReportFhirId": "843",
          "resourceType": "DiagnosticReport",
          "createdOn": "2024-12-03",
          "diagnosticUuid": "074fb161-1bca-4b72-99bc-b2e4058b38a2",
          "status": "saved",
          "documents": [
            {
              "labDocumentfhirId": "844",
              "labDocumentUuid": "558430bc-d107-4aa4-a758-5b7a3c755a16",
              "note": "xyz hahahahahha",
              "filename": "1717669846000.jpg"
            }
          ]
        },
        {
          "diagnosticReportFhirId": "846",
          "resourceType": "DiagnosticReport",
          "createdOn": "2024-12-03",
          "diagnosticUuid": "2c0af899-9d96-499f-8574-7ff9f8ac40f5",
          "status": "deleted",
          "documents": [
            {
              "labDocumentfhirId": "847",
              "labDocumentUuid": "45c7a022-7c02-4a4e-be65-96259e414feb",
              "note": "lab report test 1",
              "filename": "1717669846000.jpg"
            }
          ]
        }
      ]
    }
  ]
}
```


## Update Notes in an uploaded lab Test document
- refer this [document](/facade-api-docs/update-document-notes.md)


## Delete Lab Report : 
> DELETE : {{URL}}/v1/sync/DiagnosticReport

- This API will delete the Lab report. As only 1 file will be linked to a DiagnosticReport resource, hence directly deleting the DiagnosticReport will delete the Diagnostic report resource and linked Document Reference resource.

#### Request Body : 
- Request body array will have ids of prescription i.e `diagnosticReportFhirId` which we get in GET API response of Lab reports. This id is basically the id of newly created DiagnosticReport resource.
```json
[
  843, 846
]
```

#### Response body : 
```json
{
  "status": 1,
  "message": "Data deleted successfully.",
  "data": [
    {
      "status": "204 No Content",
      "id": null,
      "err": null,
      "fhirId": "843"
    },
    {
      "status": "204 No Content",
      "id": null,
      "err": null,
      "fhirId": "846"
    }
  ]
}
```
