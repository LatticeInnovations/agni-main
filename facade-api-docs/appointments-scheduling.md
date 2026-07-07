# Appointment and Scheduling
!!! TODO
Transfer content from the internal [Google document](https://docs.google.com/document/d/1tea1vF-fFNjooZUyRevXdJbL7an9FpN_W_IMKyF-xYE/edit), which is not publicly accessible. Remove this message once done.
!!!

## 1. Create Schedule 
> POST: `/sync/Schedule`

- API core task ( for backed purpose) : 
  - `Schedule` resources will be created with start and end time in 30-minute intervals for an organization id.
  - The organization id will be used to fetch the location id of that organization to get the resource id of the location and store it in schedule resource as reference.
  - uuid will be used for the frontend to map uuid with FHIR id for synced schedule.
  - update/create functionality will be used with combination of date time and organization to avoid redundant data and sync error.

```json Request body
[{
	"uuid": <uuid>,
	"planningHorizon": {
      "start" : "2013-12-25T09:15:00+05:30",
      "end" : <date>
  },
  "orgId": <integer> // FHIR Id of organization
}]
```

```json Response body
{
  "status" : 1,
  "message" : "data created" 
  data: [
	  {
		  "status": "201 Created",
      "fhirId": "40670",
      "id": "f8cf0c06-8d9e-4b1e-a0c4-9fab28cdc729",
      "err": null
    }
  ]
}
```

## 2. Get Schedule
To get the list of schedules of an organization. Since the numbers of schedules in a year are limited, it is synced at once, without pagination.

> GET : /Schedule

- Query Params : 
  - `Date` - to filter on date as `date` ex: `/Schedule?date=2013-12-25`
  - `orgId` - Fetch the schedule of the organization in which the practitioner works
  - `orgId` & `date` combination
  - `_lastUpdated` can be used to sync after the data has been already synced of past days for the first time.
  - `_offset`, `_count` parameters can be used for syncing the data using pagination

```json Response body
{
    "status": 2,
    "message": "Data fetched",
    "total": 5,
    "data": [
        {
            "scheduleId": "24479",
            "uuid": "ed437647-9ddb-4c4a-9e36-a4467e2100a0",
            "planningHorizon": {
                "start": "2023-11-07T09:00:00+05:30",
                "end": "2023-11-07T09:29:59+05:30"
            },
            "orgId": "22539",
            "active": true,
            "locationId": "22540",
            "bookedSlots": 0
        },
        {
            "scheduleId": "24480",
            "uuid": "3d554a88-b6c8-4d26-89ea-efdf136bd411",
            "planningHorizon": {
                "start": "2023-11-07T09:30:00+05:30",
                "end": "2023-11-07T09:59:59+05:30"
            },
            "orgId": "22539",
            "active": true,
            "locationId": "22540",
            "bookedSlots": 1
        },
        {
            "scheduleId": "24484",
            "uuid": "f5366720-9193-4b4a-a916-3cfd6fbf38ee",
            "planningHorizon": {
                "start": "2023-08-23T10:00:00+05:30",
                "end": "2023-08-23T10:29:59+05:30"
            },
            "orgId": "22539",
            "active": true,
            "locationId": "22540",
            "bookedSlots": 2
        }
    ]
}
```

### 3. Create Appointments
> POST : /sync/Appointment

- The appointment api at this stage will create Appointment resource for the patient’s every appointment.
- Slot resources will be created and lined with schedule and appointment resources.
- Update/create functionality will be used with a combination of patientid, organization id and slot id to avoid redundant creation.
- Since there can be 84 -16 appointments in a day assuming inclusion of 30 scheduled appointments. IT can lead to an average of 100 appointments created in a day, leading to a total of 3000 creations a month.
- It is better to sync 50 from the first data synced date.

| status for request body |
|--------|
|arrived|
|walkin|
|scheduled|
|noshow|
|cancelled|

```json Request body
[{
  "uuid" : "uuid",
  "patientId" : <integer>,
  "scheduleId" : <integer>,
  “slot”: {
    "start" : <date>,
    "end" : <date>,
  },
  "orgId" : <integer>,
  "createdOn" : <date>,
  "status" : <code>
}]
```

```json Response body
{
  "status" : 1,
  "message" : "data saved successfully" 
  data: [
    {
      "status": "201 Created",
      "fhirId": "40670",
      "id": "f8cf0c06-8d9e-4b1e-a0c4-9fab28cdc729",
      "err": null
    }
  ]
}

```

### 4. Get Appointments : 
> GET : /Appointment

- Get appointment list of all the patients
- Query params for filter
  - Filter by `patient id` 
  - `orgId` - It is better to sync the appointments based on organization id as other organization’s appointment is not required
  - `_lastUpdated` can be used to sync after the data has been already synced of past days for the first time.
 
#### Response body

```json
{
  "status": 1,
  "message": "Data fetched",
  "total": 2,
  "data": [
    {
      "appointmentId": "24482",
      "uuid": "f53da004-10f9-4caa-99cd-7c826b029383",
      "slot": {
        "start": "2023-11-07T09:30:00+05:30",
        "end": "2023-11-07T09:35:00+05:30"
    },
      "patientId": "24476",
      "locationId": "22540",
      "createdOn": "2023-08-22T15:12:00+05:30",
      "slotId": "24481",
      "orgId": "22539",
      "status": "scheduled",
      "scheduleId": "24480"
    },
    {
      "appointmentId": "24486",
      "uuid": "5a0e786f-c18a-4926-ae9f-ea527dc66bb2",
      "slot": {
        "start": "2023-08-23T10:08:00+05:30",
        "end": "2023-08-23T10:13:00+05:30"
      },
      "patientId": "24086",
      "locationId": "22540",
      "createdOn": "2023-08-23T10:08:54+05:30",
      "slotId": "24485",
      "orgId": "22539",
      "status": "completed",
      "scheduleId": "24484"
    }
  ]
}
```

### 5. Sync Appointments : 
> PATCH : /sync/Appointment

- When we cancel or re-schedule an appointment, we are changing or freeing the slots
  - When an appointment is canceled the slot resource of that time will be deleted and subsequent status changes will be made in the appointment resource.
  - If an appointment is rescheduled in that case the old slot resource will be updated with the new time and schedule id and createdOn thereby also changing the status of appointment back to scheduled

- Patching should not be allowed for syncing of 200 appointments in an organization

#### Request body

```json
[{
  "appointmentId" : "integer",
  "status" : {
    "operation" : "replace",
    "value": "code"
  },
  "slot" :   {
    "operation" : "replace",
    "value" : {
      "start" : "date",
      "end" : "date",
    }
  },

  "scheduleId" : {
    "operation" : "replace",
    "value" : <integer>
  },
  “createdOn” : {
    "operation" : "replace",
    "value" : <date>
  }
}]

```

#### Response body

```json
{
  "status": 1,
  "message": "Data updated successfully.",
  "data": [
    {
      "status": "200 OK",
      "fhirId": "108",
      "id": null,
      "err": null
    }
  ]
}
```

## Constraints
- Since appointments are booked offline, there is a possibility that more than 5 slots per schedule can be present, as the appointments can be created with different devices and are not synced realtime
- Same is the issue with scheduled appointments. As mentioned in the scope that a day can have not more than 16 appointments (i.e 25% of 1 schedule, so 1 out of 5 pre booked appointments).
- Appointments can only be booked one day in advance. In case the data is not synced there is a possibility of more than 16 scheduled appointments in a day.
- Backend will not maintain any restriction on slots per schedule, as it can create a problem during syncing.
