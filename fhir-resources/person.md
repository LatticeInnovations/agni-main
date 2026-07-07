# Person 
This resource will be used to store the data of a Person. It references the [`Patient`](patient.md) resource.

## Reference
- FHIR R4 `Person` resource: [https://www.hl7.org/fhir/R4/person.html](https://www.hl7.org/fhir/R4/person.html)

## Resource Details
The person resource will consist only of identifiers. 

## Identification
| Option/Display       | System  |  
| :---:                | :---:  | 
| Passport ID	         | https://www.passportindia.gov.in/	  |  
| Voter ID	           | https://www.nvsp.in/	| 
| Patient ID           | https://www.acmehealthcare.com/  |

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
      "value": "A1000877", //passport id
      "system": "https://www.passportindia.gov.in/"
    },
    {
      "value": "TYT6877777", // voter id
      "system": "https://www.nvsp.in/"
    },
    {
      "value": "CVVVGFDDFG", //patient id
      "system": "https://www.acmehealthcare.com/"
    }
  ],
  "link": [
    {
      "target": {
        "reference": "Patient/9fd282c4-b357-4e0c-b1fb-c8ba61b30e30"
      },
      "assurance": "level3"
    }
  ],
  "resourceType": "Person",
  "id": "46e32b9d-3cec-4b23-a6a9-22a34dc49a91"
}
```
