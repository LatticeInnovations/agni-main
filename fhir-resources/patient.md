---
order: 900
---

# Patient 
This resource will be used to store the data of a Patient.

## Reference
- FHIR R4 `Patient` Resource: [https://hl7.org/fhir/R4/patient.html](https://hl7.org/fhir/R4/patient.html)

## Basic Information
### Gender 
| Option/Display     | Code   |  
| :--                | :--    | 
| Male	             | male	  |  
| Female	           | female	| 
|Other               |   other|

## Identification
| Option/Display      | System  |  
| :--                 | :--  | 
| Passport ID	        | https://www.passportindia.gov.in/	  |
| Voter ID	          | https://www.nvsp.in/	| 
| Patient ID          | https://www.acmehealthcare.com/  |


## Resource Example 
```json
{
  "identifier": [
    {
      "type": {
        "coding": [
          {
            "system": "http://terminology.hl7.org/CodeSystem/v2-0203",
            "code": "MR"
          }
        ]
      },
      "system": "https://www.thelattice.in/",
      "value": "9fd282c4-b357-4e0c-b1fb-c8ba61b30e30"
    },
    {
      "value": "A1000877",
      "system": "https://www.passportindia.gov.in/"
    },
    {
      "value": "TYT6877777",
      "system": "https://www.nvsp.in/"
    },
    {
      "value": "CVVVGFDDFG",
      "system": "https://www.acmehealthcare.com/"
    }
  ],
  "name": [
    {
      "given": [
        "Vikram",
        "Kumar"
      ],
      "family": "Pandey"
    }
  ],
  "link": [],
  "telecom": [
    {
      "system": "phone",
      "value": 1234565432,
      "rank": 1
    },
    {
      "system": "email",
      "value": "vikram@example.com"
    }
  ],
  "address": [
    {
      "use": "home",
      "line": [
        "A 54 , Maya Vihar",
        "Kalkaji Extension"
      ],
      "city": "Delhi",
      "district": "East Delhi",
      "state": "Delhi",
      "postalCode": "110093",
      "country": "India"
    }
  ],
  "active": true,
  "gender": "male",
  "birthDate": "1999-03-01",
  "resourceType": "Patient"
}
```
