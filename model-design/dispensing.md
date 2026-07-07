# Dispensing medicines
!!!
Data and workflow model using FHIR
!!!

## Design insights and the Pharmacist role
The design insights from the [`Dispensing`](/user-stories/04-dispensing.md) informs what the pharmacist should be able to do. In summary, the pharmacist should be able to:
1. Create a dispensing record directly from a prescription.
1. Dispense all or part of what has been prescribed.
2. Adjust what is dispensed, as long as it does not change the dose or the active ingredient.
3. Dispense over-the-counter (OTC) medication.
4. See and update inventory; use inventory data to aid dispensing decisions.
5. Issue invoices and collect payments

!!!
The last two activities—inventory management and billing—are outside the scope of Agni. Agni should facilitate these activities, by providing suitable FHIR interfaces. 
!!!

## Implementing the scope via FHIR
FHIR provides us with the [`MedicationDispense`](https://www.hl7.org/fhir/medicationdispense.html) resource to capture dispensing of medicines by the Pharmacist, for future consumption by a Patient.
1. Searching for prescriptions: Pharmacists start their journey from the Prescription step. Just like a front-office, they need a view which consolidates recent prescriptions. 
2. Master list: The also need access to a master list of patients, much like the front office. This is because the pharmacy also operates as an independent counter that patients visit directly. This list should have filters by fields such as name, IDs, and date of last interaction. 
3. Converting prescriptions into dispensing records: A prescription groups `MedicationRequest` instances, and each instance contains details of a single medicine. Each `MedicationRequest` instance can be mapped 1:1 to a `MedicationDispense` instance, because the former contains all the clinical information needed to create the latter.
4. Dispensing multiple medicines at the same time: Just as prescriptions contain multiple `MedicationRequest` instances, pharmacists also need to create multiple `MedicationDispense` instances at the same time. This shall be accomplished by grouping all such instances within a single `Encounter` instance.
5. Validating dispensing records against prescription: This is addressed in detail in the next section.
6. Adding notes: The pharmacist shall be able to add notes to the `Encounter`, and to individual line items.
7. Dispensing over-the-counter (OTC) medicines: The system shall allow the Pharmacist to dispense OTC medicines concurrently with prescribed medicines. Pharmacists shall also be able to create fresh dispensing records that only contain OTC medicines, with reference to any prior prescription. 
8. Identifying OTC medicines: The app shall use visual language that clearly indicates that a particular `MedicationDispense` resource is for an OTC medicine. The system shall show an auto-generated note clarifying that they are not a part of the prescription. The Pharmacist shall be able to edit or delete this note. 
9. Patient notification - via SMS and email: The dispensing record shall be sent to the patient via SMS. Any shortfalls in supply shall be clearly mentioned in the SMS.

## Validating dispensing records against prescriptions
### A pharmacist shall be able to
1. Dispense less than the prescribed amount—even zero (i.e. not dispense against a particular line item).
2. Change the medication strength per dose—such as replacing a 5 mg tablet with two 2.5 mg tablets, or vice versa. 
3. Change the salt form of the medicine, without changing the active ingredient[^1].

### A pharmacist shall not be able to
1. Dispense in excess of the total amount prescribed, i.e. quantity per dose x number of doses. Thus, a pharmacist shall not be able to dispense 60 tabs of Amlodipine, when 1 tab x 30 days has been prescribed.
2. Dispense quantity per dose different from the prescription. Hence, against a dose of  prescription of 7.5 mg Amlodipine, while a pharmacist can supply 3 x 2.5 mg Amlodipine tablet, they cannot to supply either 1 x 5 mg tab, or 2 x 5 mg tab.

## Data considerations
There has to be a mechanism to tag whether a medicine is OTC or not.

## The `MedicationDispense` resource
The resource's complete schema is presented below; excluded elements are marked with :x:. 

Element | Comments
:-- | :--
`identifier` | FHIR's identifier for the resource instance
`basedOn`    | :x:
`partOf`     | :x:
`medication` | as implemented in `MedicationRequest`
`subject`    | `Patient`
`encounter`  | `Encounter` resource instance that groups all `MedicationDispense` that are created together.
`authorizingPrescription` | `MedicationRequest` instance that triggered this dispense. FHIR allows for `1:n`, but we shall use `1:1`. Absent for OTC medication.
`quantity`   | total count (units) dispensed, such as 10 tablets, 1 inhaler, 1 tube of cream etc.
`daysSupply` | days for which the medicine has been supplied. Applies to `MedicationRequests` with doses per day, times a particular number of days. Absent for OTC medication.
`recorded`   | :x:
`whenPrepared`   | :x:
`whenHandedOver` | Same date-time stamp as the parent `Encounter`
`receiver`   | Leave blank. This field can point to both `Patient` and `RelatedPerson`resources. The latter in case someone is picking up medication on behalf of the Patient. 
`note`       | Auto-generated for OTC medication. Can be made available for others too.
`renderedDosageInstruction` | :x:
`dosageInstruction` | :x:
`substitution`      | If yes, we will only populate the `.substitution.type` with code `EC`, or equivalent composition, from [this valueset](https://terminology.hl7.org/5.1.0/ValueSet-v3-ActSubstanceAdminSubstitutionCode.html) 

# Limitations
1. Agni shall not provide an inventory management system out-of-the-box. Custom integration is feasible. In the absence of integration, the Pharmacist shall have to consult their physical or electronic inventory records before dispensing medicines.
2. Agni shall not provide billing. This is often bundled with inventory management systems.
3. The current version of Agni shall not support medicine dispensing at the doorstep by Community Health Workers (CHWs). This feature can be developed if required by healthcare systems — it requires dispensing permissions for certain medicines to be extended to CHWs. 
4. Dispensing records shall presume that medicines have been picked up by the `Patient`. LatticeOnFHIR shall not support medicine pickup by a `RelatedPerson`

[^1]: This rule is configurable. It can be made more restrictive, so that the Pharmacist cannot change even the salt form.
