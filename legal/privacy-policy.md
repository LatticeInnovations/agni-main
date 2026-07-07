---
order: 100
---

# Privacy Policy

**Agni Platform — Privacy Policy**

*Effective date: 30 March 2026*

*Last updated: 07 July 2026*

---

## 1. Who we are
Agni is developed and maintained by **Lattice Innovations Pvt Ltd** ("Lattice", "we", "us", or "our"), a healthcare technology consulting, design and software development firm. Lattice has its registered offices at C-25, Okhla Industrial Area Phase I, Delhi - 110020, India.

This Privacy Policy explains how we collect, use, store, share and protect personal data when you use the Agni platform, including the Android mobile application, the Facade server, and any associated web portals (collectively, the "Platform").

This policy has been formulated in accordance with the **Digital Personal Data Protection Act, 2023** ("DPDP Act") and the **Digital Personal Data Protection Rules, 2025** ("DPDP Rules"), as notified by the Government of India. The full text of the DPDP Act is available on the [Ministry of Electronics and Information Technology (MEITy) website](https://www.meity.gov.in/static/uploads/2024/06/2bf1f0e9f04e6fb4f8fef35e82c42aa5.pdf), as are the [DPDP Rules](https://www.meity.gov.in/static/uploads/2025/11/53450e6e5dc0bfa85ebd78686cadad39.pdf).


## 2. Definitions
The following terms are used in this policy with the meanings assigned under the DPDP Act, 2023:

| Term | Meaning |
|------|---------|
| **Data Fiduciary** | The entity that determines the purpose and means of processing personal data. Agni is designed for use by certified health professionals operating out of government-run primary health centres. Each instance of Agni is locally owned and maintained by the deploying organization, which acts as the Data Fiduciary and is responsible for ensuring compliance with the DPDP Act. The Agni core team (Lattice Innovations) does not have access to individual deployment databases. |
| **Data Principal** | The individual to whom the personal data relates — i.e., a patient, beneficiary, or healthcare worker whose data is recorded in Agni. For children, this includes their parent or lawful guardian. |
| **Data Processor** | Any entity that processes personal data on behalf of a Data Fiduciary. |
| **Personal Data** | Any data about an individual who is identifiable by or in relation to such data. |
| **Health Data** | Any personal data relating to the physical or mental health of an individual, the healthcare services provided to them, or related administrative data — as described by the Health Data Management Policy under the Ayushman Bharat Digital Mission and the Electronic Health Record (EHR) Standards for India, 2016. |
| **Processing** | Any operation performed on personal data, including collection, storage, use, sharing, and erasure. |

## 3. Data collected by your Data Fiduciary
The Agni platform collects and processes the following categories of personal data as part of its primary healthcare workflows. All data is structured using the **HL7 FHIR** standard. This data is available to the Data Fiduciary, i.e. the entity that has deployed Agni.

### 3.1 Patient demographic data
- Full name (first, middle, last)
- Date of birth or age
- Sex at birth
- Phone number
- Email address
- Home address (address line, city, postal code)
- Government-issued identification numbers
- Institution-issues identification number, such as patient ID

### 3.2 Clinical and health data
- **Vitals**: height, weight, BMI, blood pressure, heart rate, respiratory rate, SpO2, temperature, blood glucose, total cholesterol, eye test results
- **Cardiovascular disease (CVD) risk assessments**: 10-year risk scores calculated using WHO charts, including inputs such as age, gender, smoking status, diabetic status, blood pressure and cholesterol
- **Symptoms and diagnosis records**: reported symptoms, clinical diagnoses (mapped to ICD-10 codes)
- **Prescriptions**: medication name, formulation, dosage, frequency, timing, duration, quantity prescribed
- **Drug dispense records**: dispensed medications, quantities, over-the-counter (OTC) dispensing, dispense logs, pharmacist notes
- **Vaccination records**: vaccine name, lot number, date of expiry, manufacturer, dose sequence, uploaded certification images
- **Lab test records**: uploaded images of lab test reports, associated notes
- **Uploaded prescription images**: photographs of handwritten or external prescriptions

### 3.3 Household and relationship data
- Household membership and relationships between patients (e.g., parent-child, cohabitation)
- Shared address information used to identify nearby matches

### 3.4 Healthcare worker data
- Name, phone number or email address (used for OTP-based authentication)
- Role (Community Health Worker, Nurse, Medical Officer, Pharmacist, Lab Technician, Front Office)
- Assigned catchment area and zonal unit

### 3.5 Operational data
- Appointment and queue records
- Data synchronization status and timestamps
- Device-level local database records (offline storage)


## 4. Purpose of data collection
Agni enables the Data Fiduciary to process personal data for **lawful and specific purposes** that are directly related to primary healthcare delivery. These include:

| Purpose | Description |
|---------|-------------|
| **Patient registration and identification** | To uniquely identify and register individuals within the health system, link household members, and connect with government registries. |
| **Clinical care delivery** | To record vitals, perform CVD risk assessments, manage prescriptions, dispense medications, record vaccinations, track symptoms and diagnoses, and document lab tests. |
| **Immunization tracking** | To maintain vaccination schedules based on the Indian Academy of Pediatrics (IAP ACVIP) guidelines and record administration details. |
| **Offline-first healthcare** | To store data locally on the mobile device so that clinical workflows can continue without internet connectivity, and to synchronize data with the FHIR server when connectivity is available. |
| **Access control and security** | To authenticate healthcare workers via OTP, enforce role-based and geographic data partitioning, and restrict access to relevant patient records. |
| **Public health reporting** | To enable aggregation and analysis of population health data through FHIR APIs that can connect with dashboards such as DHIS-2. |
| **System administration** | To manage catchment areas, allocate healthcare workers, and maintain the operational integrity of the platform. |

Lattice does not **not** process personal data for advertising, profiling, or any purpose unrelated to healthcare delivery.

## 5. Legal basis for processing
Under the DPDP Act, 2023, personal data may be processed on the following grounds:

### 5.1 Consent
The deploying Data Fiduciary must obtain **free, specific, informed, unconditional and unambiguous consent** from each Data Principal (or their parent/guardian, in the case of children) before collecting personal data through the Platform. The consent notice must be provided in clear, plain language and must itemize the categories of data collected and the purposes for which they are used.

### 5.2 Legitimate uses without consent
The DPDP Act permits processing without explicit consent in specific circumstances, including:
- When the State or any of its instrumentalities provide healthcare services, benefits, or subsidies to the Data Principal
- When processing is necessary to respond to a medical emergency involving a threat to the life or health of the Data Principal or any other individual
- When processing is required for compliance with any law or court order

### 5.3 Children's data
For patients below the age of 18, **verifiable consent from a parent or lawful guardian** is required before any personal data is processed. The identity of the consenting adult must be verified using reliable details or virtual tokens (such as Digital Locker Service Provider), in accordance with Rule 10 of the DPDP Rules.

Healthcare providers may be exempt from certain parental consent requirements if formally notified by the Central Government under Rule 12 of the DPDP Rules, and only when processing serves essential health or welfare services in the child's best interest.

## 6. Data storage and security
### 6.1 Offline-first architecture
Agni is designed with an **offline-first** architecture. Patient data is stored locally on the healthcare worker's mobile device using a lightweight database. Data is synchronized with the central HAPI FHIR server via the Facade server on a 15-minute schedule, whenever network connectivity is available.

### 6.2 Encryption and access controls
- All data transmitted between the mobile application and the server is encrypted in transit.
- Data stored on the device and on the server is protected using industry-standard encryption mechanisms.
- Access to patient data is governed by **fine-grained access control (FGAC)** based on two dimensions: the healthcare worker's **role** and their assigned **catchment area**. This is implemented using the FHIR `PractitionerRole` resource.
- Authentication is performed via one-time password (OTP) sent to the healthcare worker's registered phone number or email address.

### 6.3 Data partitioning
Geographic data partitioning ensures that each healthcare worker can only access records within their assigned catchment area (village, PHC, or CHW area). This limits the risk of data exposure by design and complements standard encryption practices.

### 6.4 Storage location
Personal data processed through the Agni platform is stored on servers located in **India**, unless the deploying Data Fiduciary explicitly configures otherwise. Deploying zns that are designated as Significant Data Fiduciaries must ensure that personal health data is not transferred outside India, as required under Section 10 of the DPDP Act.

### 6.5 Retention
Personal data is retained for as long as it is necessary to fulfil the purposes described in this policy, or as required by applicable law. The deploying Data Fiduciary is responsible for defining and enforcing data retention schedules in accordance with the DPDP Act.

## 7. Data sharing and third parties
### 7.1 FHIR interoperability
Agni is built on the HL7 FHIR standard and provides APIs (via the Facade server) that can connect with external systems such as DHIS-2 dashboards and other health information management systems (HIMS). Any such integration must be configured and authorized by the deploying Data Fiduciary, and must comply with the DPDP Act.

### 7.2 Hub and spoke laboratory model
In the hub and spoke diagnostic model, specimen data and lab test orders may be shared between Primary Health Centres (spokes) and District Hospitals (hubs) for analysis. This data exchange is limited to what is necessary for the diagnostic purpose and is conducted within the same health system.

### 7.3 No sale of data
We do **not** sell, rent, or trade personal data to any third party. Personal data is shared only as described in this policy and only with entities that are bound by appropriate data protection obligations.

### 7.4 Lattice Innovations' role
Lattice Innovations develops and maintains the Agni software. It does **not** act as a Data Processor. Each instance of Agni is locally owned and maintained by the deploying zn, and the Agni core team does not have access to individual deployment databases. Agni is provided with tools and guidelines to mitigate security and privacy risks; proper adherence to these is the responsibility of the deploying zn. If any deploying organization separately engages Lattice or other third parties for hosting, maintenance, or support services, those engagements are governed by separate contractual arrangements and the requirements of the DPDP Act.

## 8. Rights of Data Principals

Under the DPDP Act, 2023 and the DPDP Rules, 2025, every Data Principal has the following rights:

| Right | Description |
|-------|-------------|
| **Right to information** | You have the right to know what personal data has been collected about you, why it was collected, and how it is being used. |
| **Right to access** | You may request a copy of your personal data held by the Data Fiduciary. |
| **Right to correction** | You may request that inaccurate or incomplete personal data be corrected. |
| **Right to update** | You may request updates to personal data that has changed (e.g., a new address or phone number). |
| **Right to erasure** | You may request the deletion of your personal data in certain circumstances, subject to applicable legal requirements. |
| **Right to withdraw consent** | You may withdraw your consent to the processing of your personal data at any time. Withdrawal of consent does not affect the lawfulness of processing carried out before the withdrawal. |
| **Right to nominate** | You may appoint another person to exercise your data rights on your behalf. |

The deploying Data Fiduciary is required to respond to all such requests within **ninety (90) days**, as stipulated by the DPDP Rules.

---

## 9. Data breach notification

In the event of a personal data breach, the deploying Data Fiduciary must:

1. **Inform all affected Data Principals without delay**, in plain language, explaining the nature of the breach, the likely impact on them, and the steps being taken to address the issue.
2. **Notify the Data Protection Board of India within 72 hours** of becoming aware of the breach, providing details of the breach, the potential risks, and the measures taken, along with a report of intimations given to affected individuals.

The notification to affected individuals must include contact details through which they can seek further information or assistance.

## 10. Children and persons with disabilities
### 10.1 Children
The Agni platform processes health data of children as part of immunization tracking (based on IAP ACVIP guidelines) and general clinical workflows. Verifiable parental or guardian consent is required before collecting or processing any personal data of a child (a person under 18 years of age), in accordance with Section 9 of the DPDP Act and Rules 10 and 11 of the DPDP Rules.

### 10.2 Persons with disabilities
For Data Principals who are persons with disabilities and cannot act independently, processing of personal data requires verifiable consent from their lawful guardian, as identified under the applicable laws. The identity of the guardian must be verified using reliable means.

## 11. Open-source transparency
Agni is an **open-source** project. The source code for the Android client and the Facade server is publicly available:
- Android client: [github.com/LatticeInnovations/agni-android](https://github.com/LatticeInnovations/agni-android)
- Facade server: [github.com/LatticeInnovations/agni-facade](https://github.com/LatticeInnovations/agni-facade)

This transparency allows any party to independently verify how personal data is collected, processed, stored, and secured within the Platform — consistent with the principles of openness and verifiability that underpin Agni's design.

## 12. Grievance redressal

If you have any questions, concerns, or complaints regarding the processing of your personal data, you may contact the designated grievance officer of the deploying organization (the Data Fiduciary).

Lattice Innovations can be reached at:

**Lattice Innovations Pvt Ltd**
Delhi, India
Email: `soura AT thelattice DOT in`
Website: [https://www.thelattice.in](https://www.thelattice.in)

The Data Fiduciary must publish its grievance redressal mechanism and respond to grievances within **ninety (90) days**, in accordance with Rule 14 of the DPDP Rules.

If you are not satisfied with the resolution, you may file a complaint with the **Data Protection Board of India**. Appeals against the Board's decisions may be made to the **Telecom Disputes Settlement and Appellate Tribunal (TDSAT)**.

## 13. Changes to this policy
We may update this Privacy Policy from time to time to reflect changes in the Platform, applicable law, or our data practices. We encourage you to review this policy periodically.

## 14. Applicable law and jurisdiction
This Privacy Policy is governed by the laws of India, including the Digital Personal Data Protection Act, 2023 and the Digital Personal Data Protection Rules, 2025. Any disputes arising from or in connection with this policy shall be subject to the exclusive jurisdiction of the courts in Delhi, India, and the Data Protection Board of India as applicable.