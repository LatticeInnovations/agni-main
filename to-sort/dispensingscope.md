# Pre-read
User Stories > [Dispensing](/user-stories/04-dispensing.md)

# Idea in brief
This scope document covers three actions by the Pharmacist:
1. Dispense all or part of what has been prescribed.
2. Adjust what is dispensed, as long as it does not change the dose or the active ingredient.
3. Dispense over-the-counter (OTC) medication.

# From User story to Scope
Story | Scope
:-- | :--
After leaving Dr. Sood's room, Birender walked over to the pharmacy. Imtiaz Ali, the pharmacist, asked whether Birender has just had a consultation. Birender nodded. Imtiaz then looked up recent consultations, and asked, "You are Birender, right?". | The Pharmacist should be able to see recent prescriptions, sort by date, and search by patient name and other patient identifiers. A prescription should be easily convertible into a dispensing record.
Birender remembered that Simran had handed him a slip the previous evening, with medicines that she wanted to keep handy. Birender showed the slip to Imtiaz. It said, "Paracetamol 650 mg, two strips." Not even a please or a thank you. | The Pharmacist should be able to dispense over-the-counter (OTC) medication without requiring a prescription, while fulfilling a prescription.
Imtiaz checked his stocks. He has 1,947 tablets of Paracetamol 650 mg in stock. He also has 970 tablets of Amlodipine 2.5 mg, 663 tablets of Amlodipine 5 mg, but only 78 tablets of Metformin 500 mg in stock. | `Out of scope`: Agni does not include inventory management. It shall provide master list of drugs, and a FHIR API interface with a supply chain management system.
He dispensed 90 tablets of Amlodipine 2.5 mg, 15 tablets of Metformin 500 mg and 20 tablets of Paracetamol 650 mg to Birender. | Before dispensing medicines, the Pharmacist should be able to modify items dispensed based on their availability. Substitutions that _do not_ change the active ingredient shall be allowed by the system. Also, the Pharmacist shall be able to fulfill prescription line items partially, or skip them. These differences shall be visible in the App. Finally, the Pharmacist shall _not_ be able to oversupply medicines, i.e. dispense medicines in excess of the amount prescribed.
He asks Birender to take both of his prescribed medicines after supper, so that it is easier to track. | The pharmacist shall be able to add notes to the overall dispensing record. Frequently occurring notes shall be provided in a selectable form.
While logging medicines dispensed, he changed 30 x 7.5 mg Amlodipine to 90 x 2.5 mg Amlodipine, reduced the number of Metformin tablets, and added an entry for Paracetamol. | OTC medicines shall be visually distinct in the app, and the system shall make it clear that they are not a part of the prescription.
As soon as Imtiaz saved his dispensing records, Birender got a message with the details of the Amlodipine and Metformin dispensed to him. The message also stated that there was a 15-day shortfall between the prescription and its fulfillment. | The dispensing record shall be sent to the patient via SMS. Any shortfalls in supply shall be clearly mentioned in the SMS. If a patient's email is available, the same information shall also be emailed.
Finally, Imtiaz printed out a receipt, and collected payment. Birender only paid only for the Paracetamol; the other medicines were provided at no charge by the public health system. | `Out of scope` - Agni does not integrate with billing software. It shall provide FHIR API interfaces to send dispensing details to a billing system—which may be a part of the supply chain management system referenced earlier. 

# Implementing the scope via FHIR
FHIR provides us with the [MedicationDispense](https://www.hl7.org/fhir/medicationdispense.html) resource to capture dispensing of medicines by the Pharmacist, for future consumption by a Patient.

1. Searching for prescriptions: Pharmacists start their journey from the Prescription step. Just like a front-office, they need a view which consolidates all recent prescriptions, sortable by date, and searchable by patient name and ID. 
2. Converting prescriptions into dispensing records: A prescription groups `MedicationRequest` instances, and each instance contains details of a single medicine. Each `MedicationRequest` instance can be mapped 1:1 to a `MedicationDispense` instance, because the former contains all the clinical information needed to create the latter.
3. Dispensing multiple medicines at the same time: Just as prescriptions contain multiple `MedicationRequest` instances, pharmacists also need to create multiple `MedicationDispense` instances at the same time. This shall be accomplished by grouping all such instances within a single `Encounter` instance.
4. Validating dispensing records against prescription: This is addressed in detail in the next section.
5. Adding notes: The pharmacist shall be able to add notes to the `Encounter`, and to individual line items.
6. Dispensing over-the-counter (OTC) medicines: The system shall allow the Pharmacist to dispense OTC medicines concurrently with prescribed medicines. Pharmacists shall also be able to create fresh dispensing records that only contain OTC medicines, with reference to any prior prescription. 
7. Identifying OTC medicines: The app shall use visual language that clearly indicates that a particular `MedicationDispense` resource is for an OTC medicine. The system shall show an auto-generated note clarifying that they are not a part of the prescription. The Pharmacist shall be able to edit or delete this note. 
8. Patient notification - via SMS and email: The dispensing record shall be sent to the patient via SMS. Any shortfalls in supply shall be clearly mentioned in the SMS.

## Validating dispensing records against prescriptions
### A pharmacist shall be able to
1. Dispense less than the prescribed amount — even zero (i.e. not dispense against a particular line item).
2. Change the medication strength per dose — such as replacing a 5 mg tablet with two 2.5 mg tablets, or vice versa. 
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
