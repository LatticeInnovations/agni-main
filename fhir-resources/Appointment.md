---
order: 1000
---

# Appointment 
This resource will be used to store an Appointment data for a particular patient.

# Resource details
- FHIR R4 `Appointment` Resource: [https://hl7.org/fhir/R4/appointment.html](https://hl7.org/fhir/R4/appointment.html)
- An `Appointment` is referenced by a [`Slot`](Slot.md), the [`Patient`](Patient.md), and the [`Location`](Location.md).

## Basic information
### Status
| Option/Display       | status | code   |  
| :--                  | :--      | :--     | 
| walkin	             | arrived  | walkin  | 
| scheduled	           | proposed | routine | 
| arrived              | arrived  | routine |
| cancelled            | cancelled | routine | 
| in-progress          | arrived  | routine |
| completed            | arrived  | routine |
| noshow               | noshow   | routine |


## Resource example 
```json
{
  "resourceType": "Appointment",
  "id": "32306",
  "meta": {
    "versionId": "1",
    "lastUpdated": "2024-02-26T07:40:19.271+00:00",
    "source": "#Lw9ROFOXO4BsVnS3"
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
      "value": "36024b0d-ec0b-4228-bfc0-0cb2bc266a1e"
    }
  ],
  "status": "proposed",
  "appointmentType": {
    "coding": [
      {
        "system": "http://snomed.info/sct",
        "code": "routine"
      }
    ]
  },
  "start": "2024-02-28T09:30:00+05:30", //start time of an appointment
  "slot": [
    {
      "reference": "Slot/32304" //referenced slot
    }
  ],
  "created": "2024-02-26T13:09:22+05:30",
  "participant": [
    {
      "actor": {
        "reference": "Patient/25416"  //referenced patient
      }
    },
    {
      "actor": {
        "reference": "Location/22345"  //referenced location
      }
    }
  ]
}
```


# State Diagram

```mermaid
flowchart LR
    Scheduled --> | Only scheduled appointment can be rescheduled. | Update
    Update --> Scheduled
    Scheduled --> | When patient walk-in, they are labelled “arrived” | Arrived
    Arrived --> Cancelled
    Scheduled --> Cancelled
    Scheduled --> No-show
    Arrived --> | Users can change state. The system also changes state during an Encounter, i.e. any interaction between the patient & practitioner.
A single Appointment instance can map to multiple Encounter instances. | In-progress
    In-progress --> | The user can mark an appointment as complete. The system does this automatically when the day is over. | Completed




    subgraph Notes
        note1["A cancelled appointment cannot be edited."]
        note2["If a patient does not show up for a scheduled appointment, then at the end of the day, their status is automatically changed to “no-show”."]
        note3["Even if an appointment is complete, more encounters on the same day can be added to it.
Hence, encounters can be linked to appointments when the patient status is Arrived, In-progress, or Completed — as long as they both start today."]
    end

    Cancelled -.-> note1
    No-show -.-> note2
    Completed -.-> note3
    

