---
order: 98
---

# Data partitioning
Access control is naturally a part of any system's security. For Agni, access control also has a utilitarian aspect: users needs access to _relevant_ data, _quickly_. By partitioning data based on a user's role, security and utility goals are realized in tandem.

## Geographic partitions
To define geographic partitions, we follow a tree-like hierarchy. In the Indian context, there are already administrative partitions, in the form of villages, blocks, sub-division, districts, and states. However, these administrative partitions do not map precisely to catchment areas of primary care centers (PHCs) or community health workers (CHWs), except at the most granular level—the village. A village located at the boundary of a district may be served by a PHC or CHW of the adjacent district. The same logic applies to sub-division and block boundaries.

Therefore, we treat a village as the smallest population aggregate overseen by a community health worker (CHW). 

Next, we assume that a few CHWs are linked to a primary health center (PHC), which is staffed by a medical officer (MO) and nurses. As is the case for CHWs, we assume that the catchment area for a PHC can cross administrative boundaries. The PHC's catchment area is better defined by summing up the catchment areas of all the CHWs.

## Managing catchment areas
Mapping CHWs and PHCs to their catchment areas is a critical step in configuring Agni. A master list of all villages, blocks, sub-districts and districts has to be first uploaded to the Agni web portal. System administrators (SysAdmins) can update this master data. Logical checks ensure that master data remains coherent and well-structured.

Once the master data is available, the SysAdmin can define and save catchment areas, so that it is easy to allocate CHWs and PHCs to them. Consider an CHW who handles five villages across two neighboring blocks. If this catchment area has to be transferred to another CHW, then bulk-transfer, instead of item-by-item transfer, makes the process quick and error-free. To complement this functionality, the web portal also provides views and reports that show the staffing status of all catchment areas.

Since a CHW is linked to a single PHC, the web portal allows the SysAdmin to check for “unallocated” CHWs, and for villages that have not been assigned to a PHC or a CHW.

## Access control using partitions
Access to data is controlled based on two key dimensions:
1. Catchment area to which the user is mapped
2. Role of the user: CHW, Nurse, MO, front office staff, pharmacist, and lab technician

Thus, access is governed by two of the user's attributes. This approach is called fine-grained access control (FGAC), which enables tighter access control than traditional role-based access control (RBAC).

FGAC is implemented using FHIR data structures. Specifically, we use the [`PractitionerRole`](https://www.hl7.org/fhir/practitionerrole.html) Resource to map users to a combination of their roles and the organization node to which they belong.

By limiting access based on geographic partitions, we limit the risk of data exposure by design. This complements standard data security practices of encrypted storage and transmission.

## Improved offline search
CHWs and PHC users can search their respective catchment areas when offline, and add healthcare records without worrying about connectivity.

When they are online, they can switch from local search to global search, to search for patients who are from outside their catchment area. Once a particular user adds data for a patient, that patient's records become locally available.