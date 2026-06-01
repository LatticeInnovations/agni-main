---
order: 70
---

# Referrals
[!badge variant="info" text="Under design"]

The referral module allows Practitioners to refer patients to other facilities that are better equipped to treat them. Since Agni is designed for PHCs, we plan to support two types of referrals:
1. Within-system: Facilities within the same [`Organization`](organization.md), i.e. another PHC.
2. Outside-system: Facilities outside the `Organization`, both public and private.

### Source and destination
- Source: Where the referral originates from
- Destination: The one who receives the referral

## Anatomy of a referral
### Preconditions for a referral
A referral requires an Encounter to take place. An `Encounter` is an interaction between a [`Practitioner`](practitioner.md) and a Patient, _with_ clinical intent. In Agni, the triggering `Encounter` can be a risk assessment, a consultation, or a procedure.
 
Hence, a patient cannot simply be diverted from the queue of one PHC to another. There must be a clinically meaningful interaction that initiates the referral.

### Information contained in a referral
A referral should carry the following information:
- Patient name and identifier
- Source practitioner name and identifier, and the organizational unit (i.e. PHC) with which the practitioner is affiliated at the time of generating the referral
- Destination name and identifier
- Date and time of the referral
- Content of the referral: why it is being made
- Context for the referral: relevant medical records 

The following table shows how these information fields map to the two types of referral we introduced earlier.

Information field | within-system | outside-system
:--         | :-- | :--
Patient     | ✅ | ✅
Source      | ✅ | ✅
Destination | ✅ | ❌
Date-time   | ✅ | ✅
Content     | ✅ | ✅
Context     | ✅ | ❌

An outside-system referral is like an email without a recipient or attachments. Patients take the note to whomever they wish to consult, and they carry copies of their medical records with them.

### The destination - practitioner or facility?
For within-system referrals, the destination is another facility, not a physician. Thus, even if the medical officer of a PHC is transferred, the referral remains unaffected. Also, proximity is an important consideration for patients—and in Agni, `Location` is a property of `Organization`, not [`Practitioner`](practitioner.md).

## The FHIR paradigm
The [`Appointment`](https://www.hl7.org/fhir/appointment.html) resource is well-suited for within-system referrals[^1]. FHIR R4 documentation states that "`Appointment` resources are used to provide information about a planned meeting that may be in the future or past. Examples include... a follow-up for a clinical visit..."

Using the `Appointment` resource, a [`Practitioner`](practitioner.md) can create a request for a future healthcare event in any `Location`. For referrals, the destination shall be a different facility (Location)—though we can easily grasp that the same method can be used to book a follow-up visit in the same facility.

### Notable elements of the Appointment resource
Mandatory elements are marked with an asterisk (*).  
- `.status *`: When a referral is created, this parameter shall be set to `proposed`. When the patient visit the destination facility and checks-in, this status is updated to `arrived` 
- `.description`: a human-readable summary of the source, timing, and destination of the referral
- `.note`: the clinical contents of the referral  
- `.participant*`: Each referral must have at least one participant, and either the `type` or the `actor` shall be further specified. This is a FHIR constraint. In our implementation, we shall use this element to specify both the source and the destination, by providing two objects with both `type` and `actor`, as explained in the section below.

#### Participant element
1. Source object:
   - `.participant.actor *`: The source `Practitioner`. This element also accepts a Location or HealthcareService resource.
   - `.participant.type`: `REF`, for the person initiating the referral (i.e. the source). `.type` uses the [encounter-participant-type valueset](https://www.hl7.org/fhir/valueset-encounter-participant-type.html).
2. Destination object
   - `.participant.actor *`: The destination `Location`. This element also accepts a `Practitioner` or `HealthcareService` resource.
   - `.participant.type`: `ATND`, for the overseer at the destination. Participant types are defined with Practitioners in mind, but we shall use them even when `.actor` references a Location. 

### Data access
When a patient is referred to a different Location, users mapped to that Location shall have access to the patient's records. The data payload for the patient shall be enqueued for download after the referral notification.

### Inputs for detailed documentation
- [Section 12.14.5](https://www.hl7.org/fhir/appointment.html#typical) describes status transitions in the appointment workflow. The detailed design of referral workflow implementation should utilize this section.
- The constraints that apply to the `Appointment` resource need to be kept in mind. For instance, when the `Appointment.status` element is `proposed`, it does not require a start or end time. However, once the status is updated to `arrived`, a start or end time is mandatory.

## Limitations
A broader definition of referrals includes requests for follow-up from a PHC nurse or physician to a community health worker (CHW), or vice versa. CHW-PHC interactions are yet to be added to Agni.

[^1]: Before we selected the `Appointment` resource, we evaluated other ways to implemented referrals in FHIR. The first was the `ServiceRequest` resource, designed for requests such as "a referral for a diagnostic test". Next was the `Task` resource, a state machine to handle workflow; without the necessary data fields that referrals require.