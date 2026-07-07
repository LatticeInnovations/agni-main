## Description : 
- When a user creates a medical report by uploading a document, then a new encounter is created with type `medical-report-encounter`. This encounter will have reference to the main appointment encounter. 

```json
{
      "resourceType": "Encounter",
      "id": "887",
      "meta": {
        "versionId": "2",
        "lastUpdated": "2024-12-08T11:07:13.971+05:30",
        "source": "#dnSdz67cwG1wlwfo"
      },
      "status": "entered-in-error",
      "type": [ {
        "coding": [ {
          "system": "http://your-custom-coding-system",
          "code": "medical-report-encounter",
          "display": "medical Report encounter"
        } ]
      } ],
      "subject": {
        "reference": "Patient/7"
      },
      "participant": [ {
        "individual": {
          "reference": "Practitioner/2"
        }
      } ],
      "period": {
        "start": "2024-12-08",
        "end": "2024-12-08"
      },
      "serviceProvider": {
        "reference": "Organization/1"
      },
      "partOf": {
        "reference": "Encounter/75",
        "display": "Primary Encounter"
      }
    }
```
