---
order: 400
---

# Medical record
Medical records store lab test results.

## Create a Medical Record
!!!
POST `{{url}}/sync/DocumentManifest`
!!!

```json Request body
[
  {
    "medicalReportUuid": "9f5f83ce-5b58-42c7-ba21-140e0044134d",
    "appointmentId": "74",
    "patientId": "7",
    "createdOn": "2024-10-09",
    "files": [ 
      {
        "medicalDocumentUuid": "c226a99c-cc3e-4e87-90d7-cb7b7c1f9de6",
        "filename" : "1717669846000.jpg",
        "note": "example 1113"
      }
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
      "id": "9f5f83ce-5b58-42c7-ba21-140e0044134d",
      "files": [
        {
          "medicalDocumentfhirId": "853",
          "medicalDocumentUuid": "c226a99c-cc3e-4e87-90d7-cb7b7c1f9de6"
        }
      ],
      "err": null,
      "fhirId": "852"
    }
  ]
}
```



## View Medical Record  :
!!!
GET: `{URL}/DocumentManifest`
!!!

If `medicalRecord.status` is `deleted`, then the respective resources have been deleted. They have to be removed from the client during the next sync.

#### Response : 
```json
{
  "status": 1,
  "message": "Data fetched",
  "total": 1,
  "data": [
    {
      "appointmentUuid": "1233324fdf-sfaasdfaf-asd-bjadzvcoiwqoi-iuweqsnf",
      "appointmentId": "74",
      "patientId": "7",
      "generatedOn": "2024-10-11",
      "medicalRecord": [
        {
          "medicalRecordFhirId": "855",
          "resourceType": "DocumentManifest",
          "createdOn": "2024-10-09",
          "medicalReportUuid": "4f4b045a-eade-4f24-8e1f-d08537118922",
          "status": "deleted", // status will be `saved` or `deleted` only
          "documents": [
            {
              "medicalDocumentfhirId": "856",
              "medicalDocumentUuid": "10468896-0549-463c-878a-8b47f64ceb5b",
              "note": "example 1113",
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
Refer to [Update document notes](/facade-api-docs/update-document-notes.md).


## Delete medical record 
!!!
DELETE: `{{URL}}/v1/sync/DocumentManifest`
!!!

This API deletes the medical record. Since only one file is linked to a `DocumentManifest` resource, hence directly deleting the DocumentManifest asset will delete the DocumentManifest resource and linked Document Reference resource.

The Request body array has ids of prescriptions, i.e the `medicalRecordFhirId`, which we fetch via the GET API response of Lab reports. This is also the id of `DocumentManifest` resource.
```json Request Body
[
  854
]
```

####  
```json Response body 
{
  "status": 1,
  "message": "Data deleted successfully.",
  "data": [
    {
      "status": "204 No Content",
      "id": null,
      "err": null,
      "fhirId": "854"
    }
  ]
}
```