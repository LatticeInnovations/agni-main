## Description : 
- When a user creates a lab report by uploading a document, then a new encounter is created with type `lab-report-encounter`. This encounter will have reference to the main appointment encounter. 


```json
{
      "resourceType": "Encounter",
      "id": "884",
      "meta": {
        "versionId": "1",
        "lastUpdated": "2024-12-08T10:37:16.430+05:30",
        "source": "#uIRNLXSLdHWmj775"
      },
      "status": "planned",
      "type": [ {
        "coding": [ {
          "system": "http://your-custom-coding-system",
          "code": "lab-report-encounter",
          "display": "Lab Report encounter"
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
