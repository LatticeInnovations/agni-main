# Resolving race condition
- On October 24, 2024, we encountered a race condition in our API synchronization from the app.
- The first resources to be synced are the schedule and appointments, specifically those with a walk-in status.
- The issue arises when the remaining resources are synchronized asynchronously with the server.
- When all resources are synced simultaneously, we need to change the appointment status from `planned` to `in-progress` - for the app to recognize it as the last seen.
- All APIs, including vitals, symptoms and diagnosis, prescriptions, and dispense, first fetch the encounter resource - with the current status.
- Each API receives version ID: 1 of the encounter and attempts to update the status to in-progress at the same time.
- If the vitals API successfully updates the status to in-progress, it creates a new version ID (2) of the resource, - while the other APIs continue trying to update the status on the old version ID (1), resulting in a race condition.

- The resolution is to mark the appointment as in-progress through a separate patch API from the android client itself, for only once

### API structure
!!!
PATCH `/sync/Appointment`
!!!

```json Request body
[
    {
        "appointmentId": "3918",
        "generatedOn": "2024-12-04T13:00:00+05:30",
        "status": {
            "operation": "replace",
            "value": "in-progress"
        }
    }
]
```

```json Response body
{
    "status": 1,
    "message": "Data updated successfully.",
    "data": [
        {
            "status": "200 OK",
            "id": null,
            "err": null,
            "fhirId": "3918"
        }
    ]
}
```
