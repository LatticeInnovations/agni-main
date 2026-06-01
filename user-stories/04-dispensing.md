---
order: 94
---

# Dispensing
## Previous chapter
[Consultation](04-dispensing.md)

## Chapter summary
Birender goes to the Pharmacy and get his prescription fulfilled.

## This chapter
+++ :icon-book:
After leaving Dr. Sood's room, Birender walked over to the pharmacy. Imtiaz Ali, the pharmacist, asked whether Birender has just had a consultation. Birender nodded. 

Imtiaz then looked up recent consultations, and asked, "You are Birender, right?". Birender nodded again.

+++ :icon-light-bulb:
The Pharmacist should be able to see recent prescriptions, sort by date, and filter patient records in manner similar to the [front office](/user-stories/01-walk-in-visit.md#this-chapter). A prescription should be easily convertible into a dispensing record.
+++

+++ :icon-book:
Birender remembered that Simran had handed him a slip the previous evening, with medicines that she wanted to keep handy. He pulled it up. It said, 'Paracetamol 650 mg, two strips.' Not even a please or a thank you. 

+++ :icon-light-bulb:
The Pharmacist should be able to dispense over-the-counter (OTC) medication without requiring a prescription, while fulfilling a prescription.
+++

+++ :icon-book:
Imtiaz checked his stocks. He has 1,947 tablets of Paracetamol 650 mg in stock. He also has 970 tablets of Amlodipine 2.5 mg, 663 tablets of Amlodipine 5 mg, but only 78 tablets of Metformin 500 mg in stock. He made a note to ask for Metformin to be added to next week's supply.

+++ :icon-light-bulb:
Since Agni does not include an inventory management module, it has to be able to share consumption information with the inventory management system. This means that the master list of drugs has to be common to both systems. Agni shall include its own master list, and shall have the capability of using an external master list as long as it follows the same data structure. The inventory management system shall have access to Agni's consumption data over a FHIR API interface.
+++

+++ :icon-book:
He dispensed 90 tablets of Amlodipine 2.5 mg, 15 tablets of Metformin 500 mg and 20 tablets of Paracetamol 650 mg to Birender. 

+++ :icon-light-bulb:
Before dispensing medicines, the Pharmacist should be able to modify items dispensed based on their availability. Substitutions that _do not_ change the active ingredient shall be allowed by the system. Also, the Pharmacist shall be able to fulfill prescription line items partially, or skip them. These differences should be clearly visible. Finally, the Pharmacist shall _not_ be able to oversupply medicines, i.e. dispense medicines in excess of the amount prescribed.
+++

+++ :icon-book:
Imtiaz asked Birender to take both of his prescribed medicines after supper, so that it was easier to track. 

+++ :icon-light-bulb:
The pharmacist shall be able to add notes to the dispensing record. Common instructions should be provided in a selectable form; Agni can learn from user inputs.
+++

+++ :icon-book:
While logging medicines dispensed, he changed 30 x 7.5 mg Amlodipine to 90 x 2.5 mg Amlodipine, reduced the number of Metformin tablets, and added an entry for Paracetamol. 

+++ :icon-light-bulb:
OTC medicines shall be visually distinct in the app, and Agni should make it clear that they are an add-on.
+++

+++ :icon-book:
As soon as Imtiaz saved his dispensing records, Birender got an SMS with the details of the Amlodipine and Metformin dispensed to him. The message also stated that there was a 15-day shortfall between the prescription and its fulfillment. 

+++ :icon-light-bulb:
A notification should be sent to the patient through whatever channel has been configured. It should mention any shortage in supply versus the prescription.
+++

+++ :icon-book:
Finally, Imtiaz printed out a receipt, and collected payment. Birender only paid only for the Paracetamol; the other medicines were provided at no charge by the public health system. 

+++ :icon-light-bulb:
Billing is a natural part of inventory management; Agni does not provide either. Therefore, Agni needs to support billing activities in the same way that it enables inventory management—through a FHIR API interface.
+++