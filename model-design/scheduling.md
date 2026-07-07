---
order: 80
---

# Scheduling
## Context and Objective
In India, primary care facilities typically see 20-50 patients each day. Most patients walk-in for an unscheduled appointment, usually for acute care[^1]. A few patients may have scheduled appointments — usually for those with chronic conditions like diabetes and hypertension.

Agni needs to serve both scheduled and unscheduled visits, in an intuitive and operationally-flexible manner.

## Overview
### Queue 
Even if the facility has only one healthcare professional, they shall manage a queue. A queue is necessary to see unscheduled patients in the order of their arrival. Also, those with appointments have to be enqueued once they arrive at the facility. The position of a patient in the queue shall be changeable as long as they are yet to be seen by a `Practitioner` &mdash; to address situations where one patient has to be seen more urgently than another.

### Walk-in (unscheduled) visit - scope
1. A walk-in patient shall be added to the end of the queue for that day.
2. Front-office shall be able to remove them from the queue, as long as an `Encounter` has not started.
3. Front-office shall be able to change their position in the queue. 

### Scheduled visit - how it is created
Suppose, at the end of the consultation, the doctor asks the patient to return for a checkup in 2 weeks. Then, one of two things shall happen:
1. The doctor shall directly enter follow-up date via the Android app, or
2. The patient shall convey this information to the front-office, who shall enter it into the Android app.

Once the appointment is created, the patient shall receive an SMS with the appointment date and time &mdash; if their mobile number is inputted in the system. The patient shall also receive SMS reminders 3 days and 1 day before the appointment. These reminders shall also be sent via email. The reminder schedule shall be configurable, and can change from one deployment to another.

In case the patient’s mobile number has not been entered, the system shall prompt the app user to add it while creating the follow-up appointment.

## Scheduled visit - scope
1. When a patient with a prior appointment visits the facility, their status shall be changed to indicate that they have arrived.
2. Their visit time shall be visible to the front-office.
3. Front-office shall be able to remove them from the queue, as long as an `Encounter` has not started.
4. Front-office shall be able to change their position in the queue &mdash; even if that means that they are seen later or earlier than their scheduled time. 

### Optional feature: Configuring facility hours
A facility _should_ have the ability to enter their working hours, capacity (slots per day), and holiday schedule. This feature can be developed at a later date.

If developed, access to this feature must be configurable via user roles. This configuration can be set to “all users” for the demo implementation.

## Model design
Ref:
There are four resources of interest:
* [Appointment](https://www.hl7.org/fhir/appointment.html)
* [Schedule](https://www.hl7.org/fhir/schedule.html)
* [Slot](https://www.hl7.org/fhir/slot.html)

A `Schedule` belongs to a person, facility or equipment. Because LatticeOnFHIR targets primary care, we will link `Schedule` to primary care facilities, and not to an individual workstation or `Practitioner`.

A `Slot` splits up the schedule into bookable segments. One slot can accept multiple bookings.

### Default configuration
- 16 slots of 30-minute duration each day, from 0900 hrs to 1700 hrs, 7 days a week.
- Each slot shall accommodate 5 patients — thus, we assume a maximum of 80 patients in a day, with a cycle time of 5 minutes per patient.
- 1 of 4 (25%) of slots shall be reserved for appointments. Hence, each facility shall be able to pre-book 16 appointments a day, and the remaining 64 slots shall be available for walk-ins.

## Notable Resource elements
### Appointment
Element | Purpose
:--                | :--
status             | From within the [appointmentstatus](https://www.hl7.org/fhir/valueset-appointmentstatus.html) FHIR valueset, LatticeOnFHIR shall use status `proposed`, `arrived`, `cancelled`, `noshow` and `entered-in-error`
cancellationReason | Only used for appointments that are `cancelled` or `noshow`
appointmentType    | <a href="https://terminology.hl7.org/5.1.0/ValueSet-v2-0276.html">Value sets</a> defined by FHIR to be used default value should be “ROUTINE”
description        | *not required* - appears in subject line of calendars
start              | Planned start date & time. In cases where appointments are mapped to slots, do not fill it.
end                | Planned end date & time. In cases where appointments are mapped to slots, do not fill it.
created            | To capture datetime of the appointment creation
subject            | To link `Patient` to the appointment
participant        | To link details of actor which will be location and participant type
cancellationDate   | When the appointment was cancelled

#### Statuses
- `proposed`: Applied when an `Appointment` is created, either for follow-up in the same facility, or a referral to another facility. In case of referrals, the start date and time are empty, because LatticeOnFHIR shall not support referral visit scheduling. Operationally, it is the patient who decides when to go to the other facility. 
- `arrived`: Applied whenever a patient arrives at the PHC.
- `cancelled`: Applied only to cancellations of scheduled appointments
- `noshow`: Applied automatically by the app, when the patient does not visit on the day of the scheduled visit, i.e. by 11:59 pm local time.
- `entered-in-error`: There is no user workflow that ends up in this status. However, the provision for such a status shall be retained, to enable administrators to make changes with an audit trail.

#### Exclusions
- `.recurrenceTemplate`: LatticeOnFHIR shall not support recurring appointments workflows. 
- `.serviceType`: indicates the [type of service](https://terminology.hl7.org/5.1.0/CodeSystem-service-type.html) sought; not relevant to primary care.
- `.reason`: shall not be used because the [related ValueSet](https://www.hl7.org/fhir/valueset-encounter-reason.html), a list of conditions & diseases, is principally captured in the `Encounter` resource.

#### Rules
- Only proposed or cancelled appointments can be missing start/end dates.

### Schedule
Element | Purpose
:-- | :--
actor | It shall refer to a location resource of the healthcare facility
planningHorizon | As mentioned in default configuration 

#### Exclusions
`Schedule.serviceCategory`,`Schedule.serviceType` and `Schedule.specialty` shall not be utilized as LatticeOnFHIR does not require this level of detail.

### Slot
Element | Purpose
:-- | :--
schedule  | The `Schedule` resource which is split into bookable segments by this `Slot` resource
status    | Use binding slot status as this <a href="https://www.hl7.org/fhir/valueset-slotstatus.html">definition</a> to be utilized checking availability for booking appointments
overbooked | This slot has already been overbooked, appointments are unlikely to be accepted for this time
start     | Slot start date & time, mandatory
end       | Slot end date & time, mandatory

#### Exclusions
`Slot.specialty`, `Slot.serviceType`, `Slot.serviceCategory` and `Slot.appointmentType` shall not be utilized as LatticeOnFHIR does not require this level of specificity.


## Limitations
- `Appointment` is used to book a slot, and [AppointmentResponse](https://www.hl7.org/fhir/appointmentresponse.html) is used to confirm the booking. We shall not use the `AppointmentResponse` resource because appointment confirmation lies outside the system scope. 
- If we introduce tele-medicine, then individual Practitioners shall need their own schedules. At that time, the schedule shall have to be changed from a facility-centric design to a practitioner-centric design.

[^1]: Acute care refers to immediate health needs, such as a fracture or a severe stomach ache. Chronic care is the opposite &mdash; it requires routine checkups, even when a person is “feeling fine”.

