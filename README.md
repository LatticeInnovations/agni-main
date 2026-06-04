---
title: Home
icon: home
---

# <img src="/images/logomark-light.png" alt="logo" height = "50" width="50"> What is Agni?
Agni is a mobile-first software platform that supports population-scale healthcare delivery.

:::card-grid
<div class="card-container">
<a href="/key-features/"><img src="/images/agni-key-features.jpg"></a>

**KEY FEATURES**  
[Designed for primary healthcare](/key-features/index.md)
</div>

<div class="card-container">
<a href="/user-stories/"><img src="/images/agni-user-stories.jpg"></a>

**USER STORIES**  
[Insights from the patient's viewpoint](/user-stories/index.md)
</div>

<div class="card-container">
<a href="https://play.google.com/store/apps/details?id=com.latticeonfhir.android" target="_blank"><img src="/images/agni-play-store.jpg"></a>

**TRY IT OUT**  
[Download the Android app](https://play.google.com/store/apps/details?id=com.latticeonfhir.android)
</div>
:::

## Open-source code repositories
All of our repositories are in the public domain.
- Website content and issue tracking: [https://github.com/LatticeInnovations/agni-main](https://github.com/LatticeInnovations/agni-main)
- Android client: [https://github.com/LatticeInnovations/agni-android](https://github.com/LatticeInnovations/agni-android)
- Facade server: [https://github.com/LatticeInnovations/agni-facade](https://github.com/LatticeInnovations/agni-facade)

The Facade server interfaces with a plain vanilla HAPI FHIR server, [version 6.6.0](https://github.com/hapifhir/hapi-fhir-jpaserver-starter/tree/v6.6.0), which stores data on a PostgreSQL database.

## Motivation
Specialized, facility-based healthcare presents an attractive market for health technology providers—as evidenced by the many hospital information management systems (HIMS) available today. In contrast, digital platforms for primary care are far fewer.

Primary care cannot function using a watered-down HIMS. Even though its clinical complexity is lower than that of tertiary care, primary care has its own set of needs—such as the ability to function when offline. Addressing such needs requires a first-principles approach. Furthermore, platforms for primary care have to serve a public health function. Therefore, they need to be open and transparent. 

`Openness` means it must be capable of incorporating protocols and procedures based on the needs of the health system.

`Transparency` means that its inner workings must be visible, and that it is externally verifiable—particularly when it comes to verifying how confidential health data is secured.

Both openness and transparency demand a standards-based approach. They also require—in our opinion—an open-source approach.

Agni is our attempt at applying first-principles to design and engineer a platform that is open-source, standards-based, and offline-capable. It is mobile-first: we did not want access to software to be limited by access to hardware.

Who are we? We are [Lattice Innovations](https://www.thelattice.in), a healthcare technology consulting and design firm based in Delhi, India.

## What is Agni?
Agni is a mobile-first platform that:
* is designed for [offline use](/key-features/offline-first.md),
* uses evidence-based guidelines for clinical workflows,
* is built on [HL7® FHIR®](/key-features/fhir-data-model.md), with out-of-the-box interoperability, and
* [provides APIs](/facade-api-docs/index.md) that can connect with DHIS-2 and other dashboards.

The system utilizes the WHO’s PEN protocols for cardiovascular disease (CVD) risk assessment[^1], and the Indian Academy of Pediatrics' immunization recommendations[^2]. Along with its focus on cardiac health and immunization, it provides a complete primary care workflow.

### Components
The primary worker is the mobile app. It stores data locally on a lightweight database, and syncs with the HAPI FHIR server via a FHIR facade server. We are also developing a web app that provides all the functionality that the app provides, plus platform administration capabilities.

![Components of Agni](/images/components.png)

## Why call it Agni?
The name Agni is inspired by two paradigms—old and new, Eastern and Western.

The first paradigm comes from the ancient system of _Ayurveda_. In it, Agni represents our metabolic processes—a system that needs to be in harmony to ensure health, not just remediation of disease. This focus of wellness, not just illness, is what we hope to support with our work.

The second paradigm is contemporary—the HL7® fast health interoperability resources, or FHIR®. Pronounced “fire”, which translates to Agni in many Indian languages, FHIR specifies how to structure health data, to make it easy to comprehend and exchange. Over the past decade, it has emerged as the de facto open-source standard for health data, with a global community of developers and advocates. We have built on the work done by this community, and seek to contribute our learnings to it.

## Upcoming enhancements
Our vision of a digital system is one that connects beneficiaries to healthcare professionals and the public health system, eliminates waste, and enables flow. We have started with workflows for primary health centers (PHCs). We plan to enhance features for PHCs, and add features targeted at community health workers (CHWs)—starting with offering more screening algorithms.

We have also prototyped _fully offline_ peer-to-peer communication _within_ PHC, connecting all workstations—front office, consultation, nursing, pharmacy and lab—without the need for an internet connection or a router. We will incorporate this capability into Agni based on end-user feedback.

## Legalese
### Limitation of liability
This website is provided “as is”, without warranty of any kind, express or implied, including but not limited to the warranties of merchantability, fitness for a particular purpose and noninfringement. In no event shall the authors or copyright holders be liable for any claim, damages or other liability, whether in an action of contract, tort or otherwise, arising from, out of or in connection with the website or the use or other dealings in the website.

### Disclaimer
* HL7® and FHIR® are [registered trademarks](https://confluence.hl7.org/display/FHIR/FHIR+Trademark+Policy) of Health Level Seven International. HAPI FHIR (https://hapifhir.io/) in an open-source implementation of FHIR in Java. This website is unaffiliated with HL7, FHIR, or HAPI FHIR.
* We utilize publications from the public domain, from entities such as the World Health Organization, and the Indian Association of Pediatrics. We are unaffiliated with such agencies.

### Image credits
We are glad that a resource like Unsplash exists. Here are links to the photos we used on this page:
- <a href="https://unsplash.com/@mikekilcoyne?utm_content=creditCopyText&utm_medium=referral&utm_source=unsplash">Mike Kilcoyne</a> on <a href="https://unsplash.com/photos/lighted-orange-star-night-lamp-G1y7tcQxG34?utm_content=creditCopyText&utm_medium=referral&utm_source=unsplash">Unsplash</a>
- <a href="https://unsplash.com/@introspectivedsgn?utm_content=creditCopyText&utm_medium=referral&utm_source=unsplash">Erik Mclean</a> on <a href="https://unsplash.com/photos/white-and-black-glass-window--4JVGXz1x8g?utm_content=creditCopyText&utm_medium=referral&utm_source=unsplash">Unsplash</a>
- <a href="https://unsplash.com/@pcbulai?utm_content=creditCopyText&utm_medium=referral&utm_source=unsplash">Paul Bulai</a> on <a href="https://unsplash.com/photos/flame-illustration-XOQJa4OC8P0?utm_content=creditCopyText&utm_medium=referral&utm_source=unsplash">Unsplash</a>

[^1]: [HEARTS: Risk-based CVD management](https://iris.who.int/bitstream/handle/10665/333221/9789240001367-eng.pdf), _Annex 2 and 3: WHO CVD risk charts_; World Health Organization, 2020; ISBN 978-92-4-000136-7.
[^2]: Kasi SG et al, [IAP ACVIP: Recommended Immunization Schedule (2020-21) and Update on Immunization for Children 0-18 Years](https://iapindia.org/pdf/ACVIP-recommandations-Indian-Pediatrics-January-2021-issue.pdf); _Indian Pediatrics_ 45 58(45): 2021 Jan; PII:S097475591600258
[^3]: [HEARTS: Evidence-based treatment protocols](https://iris.who.int/bitstream/handle/10665/260421/WHO-NMH-NVI-18.2-eng.pdf), _Hypertension detection and treatment_; World Health Organization, 2018; WHO/NMH/NVI/18.2.
