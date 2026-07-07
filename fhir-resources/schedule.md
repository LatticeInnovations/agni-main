# Schedule 
The `Schedule` resource provides containers of time, or time-windows, that can be booked using an [`Appointment`](appointment.md). The time period contained in a schedule can be further subdivided using [`Slots`](Slot.md).

 In Agni, schedules are specific to a health facility. More generally, schedules can be created for any service or resource—such as practitioners, departments, rooms, or equipment. 

## References
- FHIR R4: [https://hl7.org/fhir/R4/schedule.html](https://hl7.org/fhir/R4/schedule.html)

## Basic Information
- Each day will be subdivided into 16 units of 30 minutes each, starting from 9:00 AM to 4:30 PM.
- This 30-minute interval is subdivided into [Slots](slot.md)
- Each schedule must be referenced to a Location

## Resource Example 
```json
{
  "resourceType": "Schedule",
  "id": "32352",
  "meta": {
    "versionId": "1",
    "lastUpdated": "2024-02-27T05:40:04.355+00:00",
    "source": "#OnP7fcSbaziaW125"
  },
  "identifier": [
    {
      "type": {
        "coding": [
          {
            "system": "http://terminology.hl7.org/CodeSystem/v2-0203",
            "code": "U"
          }
        ]
      },
      "system": "https://www.thelattice.in/",
      "value": "cccd5efd-1483-43fd-a6de-fff1a93153bd"
    }
  ],
  "active": true,
  "actor": [
    {
      "reference": "Location/22345" // reference to the organization or location
    }
  ],
  "planningHorizon": {
    "start": "2024-02-28T09:00:00+05:30", //start date-time of schedule
    "end": "2024-02-28T09:29:59+05:30" // end date-time of schedule
  }
}
```
