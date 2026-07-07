# RelatedPerson 
This resource will be used to store the data of a Related Person to a Patient, which will reference another Patient resouce of linked Patient.

# Resource Details
> Related Person resource will consist Patient Reference and the relationship.

| Relationship    | code  |  
| :---:                | :---:  | 
| Father	             |     |  
| Mother	             | 	   |  
| Son                  |     |
| Grand Father                  |     |
| Brother                  |     |
| Grand Son                  |     |
| Uncle | |
| Brother in law |   |
| father in law |    | 
| Son in law |     | 
| Nephew  |     | 
| Husband    |     | 

# Resource Example 
```
{
        "resourceType": "RelatedPerson",
        "id": "32536",
        "meta": {
          "versionId": "1",
          "lastUpdated": "2024-02-29T06:52:00.529+00:00",
          "source": "#nrbvKPLKyiyM6DRE"
        },
        "patient": {
          "reference": "Patient/32534"
        },
        "relationship": [
          {
            "coding": [
              {
                "system": "http://terminology.hl7.org/CodeSystem/v3-RoleCode",
                "code": "FTH"
              }
            ]
          }
        ]
      }
```
