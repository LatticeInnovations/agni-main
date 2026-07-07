## Overview
- This consist of medication Request / Prescription where user can upload a photo for prescription.

## Resource Example : 

```json
{
  "resourceType": "MedicationRequest",
  "id": "764",
  "meta": {
    "versionId": "1",
    "lastUpdated": "2024-12-02T20:43:24.210+05:30",
    "source": "#SIeNIYWxu58cdza4"
  },
  "identifier": [
    {
      "system": "http://lattice.in/sid/medRequest",
      "value": "ac129af4-d595-4d85-865b-d9afa236a0bd"
    }
  ],
  "intent": "order",
  "subject": {
    "reference": "Patient/13"
  },
  "encounter": {
    "reference": "Encounter/763"
  },
  "supportingInformation": [
    {
      "reference": "DocumentReference/765"
    },
    {
      "reference": "DocumentReference/766"
    }
  ],
  "groupIdentifier": {
    "system": "http://hospital.smarthealthit.org/prescriptions",
    "value": "00013"
  }
}
