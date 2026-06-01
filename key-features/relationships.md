---
order: 94
---

# Representing relationships
One of the unique features of Agni is its ability to relate individuals to one another.

Relationships can be seen from three perspectives—each with public health implications:
1. _Genetic relationships_, such as that between a biological mother and daughter, can be used to assess risk for diseases with a hereditary component, such as cardiovascular disease (CVD) and diabetes.
2. _Cohabitation_ information, such as two friends sharing an apartment, or children going to the same classroom, can be used to assess risk of infectious diseases, such as COVID-19 and Tuberculosis.
3. _Legally-related_ individuals, such as a couple and their adopted child, has administrative utility. They may form an administrative entity for various government programs, across health, nutrition, and social protection.

It is quite common that all three types intersect: legally- and biologically-related individuals often cohabit.

## Agni's approach: relationships as a separate entity
Agni uses the term `household` to define a group of related individuals.

It stores patient records and relationship data separately, so that each individual remains an independent entity—removing one record or relationship does not impact another. 

This is illustrated below, with an example of a family consisting of a mother and her son, both of whom are part of a government registry. Every member of the registry—whether or not they have an electronic medical record—is uniquely identified in Agni using a [`Person`](/fhir-resources/person.md) resource. This linkage allows Agni to "know the denominator", i.e. enumerate the population.

When an individual receives healthcare services for the first time, Agni creates a [`Patient`](/fhir-resources/patient.md) resource based on the `Person` resource. Concurrently, Agni creates a [`RelatedPerson`](/fhir-resources/related-person.md) resource, which stores the relationship between both objects. Each relationship is stored as a separate entity — one pointing from Mother to Son, and the other from Son to Mother.

![Example of how relationships are tracked in Agni](/images/representing-relationships-in-fhir.png)

This design serves as a backbone that can be used to engineer more complex features—such as updating an individual's cardic risk profile based on their biological parents’ medical history.

## The ephemeral household
A household does not have its own identity; it is exists as long as the connections between its members exist. Even address is a property of an individual, and multiple individuals can have the same address. 

This is helpful when household members relocate, households split, or new households form. An individual can be uniquely tracked as they navigate a changing web of relationships.

In case a health system requires a persistent, unique identifier for a household, then Agni has to be redesigned, and the `Group` FHIR resource has to be put to use.