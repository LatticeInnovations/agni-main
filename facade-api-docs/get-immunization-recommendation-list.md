## Get Immunization Recommendation List : 
> [!NOTE]  
> We will not use this, as we will need to find all patients first at backend and then find their Immunization Recommendation resource. Also using this method we won't have any control in using pagination as the count of response data will not be accurate.

> Endpoint : GET /v1/ImmunizationRecommendation
- This is to fetch all records of this resource.

> Endpoint : GET /v1/ImmunizationRecommendation?patient=1212,1111,9898
- This will fetch all `ImmunizationRecommendation` resource of given patients.
> [!NOTE]  
> Frontend needs to request this resource by using patient ids in query params. Frontend must send max of 10 patient ids at a time. No pagination is supported in this query, it will totally depend on the patient ids sent in the query params.

## Query params : 
#### Response body

```
{
  "status": 1,
  "message": "Data fetched",
  "total": 2,
  "data": [
    {
      "patientId" : 1
      "vaccine": "Bacillus Calmette-Guerin vaccine",
      "vaccineText" : "BCG",
      "vaccineCode" : "19",
      "seriesDoses": 3,
      "doseNumber" : 1,
      "vaccineStartDate" : "2025-03-10T10:15:30.123Z",
      "vaccineEndDate" : "2025-04-10T10:15:30.123Z",
      "vaccineBufferDate" : "2025-06-02T10:15:30.123Z"
      "vaccineDueDate" : "2025-04-10T10:15:30.123Z"
    },
    {
      "patientId" : 1
      "vaccine": "Bacillus Calmette-Guerin vaccine",
      "vaccineText" : "BCG",
      "vaccineCode" : "19",
      "seriesDoses": 3,
      "doseNumber" : 2,
      "vaccineStartDate" : "2025-03-10T10:15:30.123Z",
      "vaccineEndDate" : "2025-04-10T10:15:30.123Z",
      "vaccineBufferDate" : "2025-06-02T10:15:30.123Z",
      "vaccineDueDate" : "2025-04-10T10:15:30.123Z"
    }
  ]
}
```
