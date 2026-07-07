# Practitioners
A primary healthcare system delivers services through care providers, or practitioners, who play a variety of roles, such as:
- Doctor
- Nurse
- Pharmacist
- Lab technician
- Front-office staff 
- Paramedics

Individual identities of these practitioners, along with their roles, have to be associated with the [organization](organization.md) under whose aegis they deliver healthcare services.

## The FHIR paradigm
FHIR provides the [`Practitioner`](https://www.hl7.org/fhir/practitioner.html) resource for this purpose. The `Practitioner` resource attributes activities and responsibilities to all individuals who are engaged in the healthcare process and healthcare-related services as part of their formal responsibilities. The `Practitioner` resources can be thought of as the mirror of the `Patient` resource.

In the LatticeOnFHIR implementation, a `Practitioner` shall require an `Organization` resource to exist first.

Also, in the LatticeOnFHIR implementation, we shall only use the "usual" parameters, such as name, gender, age, and contact information. Parameters to capture qualifications of the practitioner, such as `.qualification.code` and `.qualification.period`, shall not be used.

### Connecting Practitioners to Organizations using PractitionerRole
The [`PractitionerRole 🔗`](https://www.hl7.org/fhir/practitionerrole.html) resource describes the types of services that practitioners provide for an organization at specific location(s). It includes the following parameters:
- `.practitioner`: reference to the `Practitioner` resource
- `.organization`: reference to the `Organization` resource
- `.code`: roles which the practitioner may perform, from the [practitioner-role valueset 🔗](https://www.hl7.org/fhir/valueset-practitioner-role.html). We shall use the code `ict` to refer to non-clinical staff who use information and communication technologies (ict) to manage patient records.
- `.location`: locations where the practitioner provides services

We shall NOT use the`.location` element. A practitioner's location shall be derived only from the location of the `Organization` that they are connected to, via the `PractitionerRole` resource.

If a practitioner works in multiple organizations — say, PHC 1 and PHC 2 — then they will have multiple instances of `PractitionerRole` resources; one for each practitioner-org relationship.

### Some nuances 
Many resource types have a choice of a reference to either a Practitioner resource or a PractitionerRole resource. The latter provides organizational context for the practitioners participation when it is required, otherwise a direct reference to the practitioner may be used.

For use cases where an organization has activities where a practitioner is not defined/pre-allocated for a specific role (e.g. an un-named surgeon at XYZ Hospital), a PractitionerRole resource can be used with an empty Practitioner property, and the other relevant role properties populated — i.e. code, organization.

## Limitation: Practitioner not mapped to Person
In a public health system, practitioners can also be patients, because the system covers the entire population of a region or country. Ideally, when a practitioner seeks healthcare services, their `Patient` record should point to their `Practitioner` record via their `Person` record. Each instance of `Person` instance can then uniquely identify an individual.

However, the utility of this association unclear. Even if a system duplicates the same person's data as both a patient and practitioner, connecting the two records does not support existing use cases. Also, this feature is complex to implement, and can easily confuse users. It complicates the "add patient" workflow — users need a separate mechanism to add practitioners as patients.

Hence, we shall not map practitioners to `Person` instances.

## Assumption: one smartphone, one practitioner
Agni assumes that each user has access to a separate smartphone. Smartphones are private devices by design, and the Agni app is a lightweight addition. This assumption improves both performance and security. Performance is improved because the data payload stored on the app can be optimized for one user. Security is improved because more robust access management policies can be implement when a device and its owner are uniquely mapped to one another.

As and when Agni is extended to patients, this assumption will have to be questioned. Smartphone is a shared resource is many households, and there are gender-based differences in access to them. 
