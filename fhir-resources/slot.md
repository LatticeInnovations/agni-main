# Slot 
This resource provides a unit of time that can be booked using the [`Appointment`](appointment.md) resource. Slots are a sub0-division of the [`Schedule`](schedule.md) resource.

## Reference
- FHIR R4: [https://hl7.org/fhir/R4/slot.html](https://hl7.org/fhir/R4/slot.html)

## Basic information
- Each slot is five minutes long. This is an Agni-specific design choice.
- Slots do not overlap.
- Every Slot must reference a single [`Schedule`](schedule.md) only.
- One schedule can have maximum of 5 slots. 
- The maximum number of visits can be booked in a single day is `Schedules per day` x `Slots per schedule`.

## Resource example 
```json
{
  "resourceType": "Slot",
  "id": "32305",
  "meta": {
    "versionId": "1",
    "lastUpdated": "2024-02-26T07:40:19.271+00:00",
    "source": "#Lw9ROFOXO4BsVnS3"
  },
  "schedule": {
    "reference": "Schedule/32303" //referenced schedule
  },
  "status": "free",
  "start": "2024-02-26T13:10:00+05:30",
  "end": "2024-02-26T13:15:00+05:30"
}
```
