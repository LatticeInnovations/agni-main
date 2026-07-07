---
order: 700
---

# Prescription upload
## Description
Users can choose to take a photo of a prescription, instead of typing it in. On upload, three resources are created, `Encounter`, `DocumentReference` and `MedicationRequest`.
- A child [`Encounter`](/fhir-resources/prescription-encounter-document.md) that references the main (parent) appointment encounter
- [MedicationRequest](/fhir-resources/medication-request-photo-upload.md) that references the `DocumentReference`.
- [DocumentReference](/fhir-resources/document-reference.md) that stores the filename and the notes.

## Create a Prescription
!!!
POST: `{{URL}}/v1/sync/PrescriptionFile`
!!!

```json Request body
[
  {
    "appointmentId": "74",
    "patientId": "13",
    "generatedOn": "2024-12-02T17:00:00+05:30",
    "prescriptionId": "f7c6c69e-93f8-41c0-8782-e2c1c10f4dcd",
    "prescriptionFiles": [
      {
        "documentUuid": "02ee533b-cbb0-4a63-9829-585e8951771d",
        "filename": "3423432424545.jpeg",
        "note": "example 1"
      },
      {
        "documentUuid": "8fe48c2e-a749-4a60-989d-3fdbe3ba0d0c",
        "filename": "34234324265656.jpeg",
        "note": "example 2"
      }
    ]
  },
  {
    "appointmentId": "74",
    "patientId": "13",
    "generatedOn": "2024-12-03T17:00:00+05:30",
    "prescriptionId": "80c889d6-6753-44f5-9da2-888ab7274e60",
    "prescriptionFiles": [
      {
        "documentUuid": "4c9a64fe-cf32-420a-b5b8-07cc4724d206",
        "filename": "3423432424545.jpeg",
        "note": "example 3"
      },
      {
        "documentUuid": "12069d60-e789-4c6f-af0a-60927a21c535",
        "filename": "34234324265656.jpeg",
        "note": "example 4"
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
      "id": "f7c6c69e-93f8-41c0-8782-e2c1c10f4dcd",
      "prescriptionFiles": [
        {
          "documentfhirId": "835",
          "documentUuid": "02ee533b-cbb0-4a63-9829-585e8951771d"
        },
        {
          "documentfhirId": "836",
          "documentUuid": "8fe48c2e-a749-4a60-989d-3fdbe3ba0d0c"
        }
      ],
      "err": null,
      "fhirId": "832"
    },
    {
      "status": "201 Created",
      "id": "80c889d6-6753-44f5-9da2-888ab7274e60",
      "prescriptionFiles": [
        {
          "documentfhirId": "838",
          "documentUuid": "4c9a64fe-cf32-420a-b5b8-07cc4724d206"
        },
        {
          "documentfhirId": "839",
          "documentUuid": "12069d60-e789-4c6f-af0a-60927a21c535"
        }
      ],
      "err": null,
      "fhirId": "833"
    }
  ]
}
```


## Fetch Prescription
!!!
GET: `{{URL}}/v1/PrescriptionFile?patientId=13`
!!!

Pass the patient id in the parameter to fetch the prescriptions.

```json Response body
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
      "status": "saved",
      "prescriptionFiles": [
        {
          "documentFhirId": "765",
          "documentUuid": "203a9b02-5aa0-4afa-9991-657ed3a827b5",
          "note": "this is note 1",
          "filename": "342343242.jpeg"
        },
        {
          "documentFhirId": "766",
          "documentUuid": "9fe19934-368d-4209-901d-53709d53afb5",
          "note": "",
          "filename": "342343242.jpeg"
        }
      ],
      "prescriptionDocumentFhirId": "763",
      "prescriptionId": "50023cdc-d840-4a8a-ab4d-e92eddd2c51e"
    },
    {
      "appointmentUuid": "1233324fdf-sfaasdfaf-asd-bjadzvcoiwqoi-iuweqsnf",
      "appointmentId": "74",
      "patientId": "7",
      "generatedOn": "2024-10-11",
      "status": "delete",
      "prescriptionFiles": [
        {
          "documentFhirId": "765",
          "documentUuid": "203a9b02-5aa0-4afa-9991-657ed3a827b5",
          "note": "this is note 1",
          "filename": "342343242.jpeg"
        },
        {
          "documentFhirId": "766",
          "documentUuid": "9fe19934-368d-4209-901d-53709d53afb5",
          "note": "",
          "filename": "342343242.jpeg"
        }
      ],
      "prescriptionDocumentFhirId": "767",
      "prescriptionId": "4545023cdc-asff-4a8a-ab4d-e92eddd4545e"
    }
  ]
}
```

## Update notes in an uploaded document
- refer this [document](/facade-api-docs/update-document-notes.md)

## Delete Prescription : 
> DELETE : {{URL}}/v1/sync/PrescriptionFile

- This API will delete the photo upload prescription. As only 1 files will be linked to a medication resource, hence directly deleting the prescription will delete the sub encounter, medication request resource and linked Document Reference resource.

#### Request Body : 
- Request body array will have ids of prescription i.1 `prescriptionDocumentFhirId` which we get in GET API response of prescription. This id is basically the id of newly sub-encounter created.
```json
[
  816, 812, 808
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
      "fhirId": "816"
    },
    {
      "status": "204 No Content",
      "id": null,
      "err": null,
      "fhirId": "812"
    },
    {
      "status": "204 No Content",
      "id": null,
      "err": null,
      "fhirId": "808"
    }
  ]
}
```
