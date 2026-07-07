# Walk-in visit
## Previous Chapter
None

## Chapter summary
We begin our story in May 2024, and meet our protagonist, Birender Singh. We learn about his walk-in visit to a primary health center (PHC), and the provisional diagnosis made by the PHC's medical officer, Dr. Sood.

## This chapter
+++ :icon-book:
Birender and his wife, Janaki, had lived in the small town of Tikroul their entire lives. Birender was sixty years old, with a history of high blood pressure. For the past four years, he had been on hypertensive medication.

Since early April, Birender has been waking up two to three times a night to go to the bathroom. He decided to go for a checkup to the local primary care center (PHC). He was accompanied by his daughter, Simran. She lived close by, and taught at the local school.

They arrived at the Tikroul PHC at 9:30 am. They were greeted at the front desk by Gayatri Gupta, the PHC staff nurse. Gayatri was a well-known face in the community. Every Friday evening, she ran a health education camp at the local school.
 
Gayatri searched for Birender's name, and found that he last visited the PHC a year ago. At that time, he was seen by Dr. Biswajit Pramanik, who had been replaced by Dr. Anamika Sood as the MO (Medical Officer) three months ago.

+++ :icon-light-bulb:
Most visits are unscheduled; patients visit the PHC when they feel unwell. These visits can be years apart. Therefore, front office personnel—be it a staff nurse or a receptionist—need an efficient search interface. They should be able to search for a patient in various ways—by their name, phone number, age range, ID—with the ability to combine multiple search criteria. Thus, `patient search` should be thought of as a `filter` that narrows down the entire list of patients to a few. 

The search space also becomes a key consideration; filtering a million records is time- and resource-intensive. In an offline-capable system operating at a community-level, a limited set of records should be available on the user's mobile device. This makes search more efficient, and also improves data privacy by design.
+++

+++ :icon-book:
Gayatri informed Birender and Simran that they were fourth in the queue to see the doctor. She proceeded to check Birender's weight and blood pressure. "Hmmm," she said, "Your weight has increased from 77 to 82 kgs, and your blood pressure is 145/95. Have a seat. I will re-check your blood pressure after you rest for ten minutes."

+++ :icon-light-bulb:
Front office staff need to inform patients of their position in the queue. They need a simple interface to see a consolidated queue for both walk-in and scheduled visits.
+++

+++ :icon-book:
Gayatri then turned to Simran. "Are you related to Birender?" 

"I'm his daughter," replied Simran.

"Can I link your medical records?"

"Why?"

"There are two benefits. First, we have your information as an emergency contact. Second, we are able to link his medical history to yours, which helps us assess risk of diseases like heart conditions and diabetes."

"Oh, ok. Go ahead then," said Simran.

Gayatri located Simran's medical record using her ABHA ID. After linking it to Birender's, she noticed that Simran already a record linked to hers—that of her five-year old son, Rajat. Gayatri eyed Rajat's vaccination status, and asked Simran about his health. Simran promised to bring Rajat in for a health checkup soon.

+++ :icon-light-bulb:
The need to link family members can arises as a part of healthcare and social security programs. Once records are linked, they should be bi-directionally navigable. This means that the relationship has to mirrored, i.e. if A is the daughter of B, then B is the father or mother of A.  
+++

+++ :icon-book:
Ten minutes passed quickly. Gayatri re-checked Birender's blood pressure twice, and saw that it dropped to 143/92 on average. She updated the recently created record, with a note that blood pressure was re-checked to give the patient time to rest.

+++ :icon-light-bulb:
WHO guidelines state that blood pressure should be measured once a patient is rested. In a busy environment, this may not be possible at all times. If it is feasible, then the system should accommodate it. 
+++

+++ :icon-book:
Before Gayatri could ask Birender some screening questions, Dr. Sood completed her last consultation. At the same time, another patient, Himmat Anand, walked in. Himmat was a 45-year old man. He had called the PHC the previous day to make an appointment for 10:00 am, to get a medical certificate for his new job. 

Though it was still a few minutes to 10, Himmat was insistent that he see Dr. Sood right away. "I can't be late for the first day of my new job!", he protested. Gayatri convinced him to wait, and sent Birender and Simran to the doctor.

+++ :icon-light-bulb:
Front office staff should have the ability to change the sequence of enqueued patients, so that they can exercise judgment about who sees the doctor first. Complex queueing logic is not required in a PHC. 
+++

+++ :icon-book:
When they entered the office, they saw Dr. Sood peering at her phone. She looked up as they walked in. 

"I have reviewed your last three visits, which stretch over the past four years," she said to Birender, "You have gradually gained weight. And your BP has increased from what it was in 2019, after you started your hypertension medication." 

Dr. Sood then asked Birender questions about his current health, and the reason for his visit.

+++ :icon-light-bulb:
Once a patient has been enqueued by the front office, the physician should be able to directly access the queue. This eliminates the need to search. 

Once the physician locates the patient, they must be able to see trends, and access historical records quickly.
+++

+++ :icon-book:
On learning of his recent symptoms, she suspected diabetes. She asked Birender to return the next morning, on an empty stomach, for a fasting glucose test and an OGTT[^1]. She advised him to walk at least two kilometers daily, and limit his consumption of fried and sugary foods, to keep his weight under control. Dr. Sood wrote a note, and asked Birender to show it to Gayatri on the way out.

Gayatri reviewed the note, and counseled Birender and Simran about the fasting test and OGTT. She then scheduled a follow-up visit for the next morning, at 8:00 am. As Simran accompanied Birender back to his home, he received a text message informing him of his appointment the next day.

+++ :icon-light-bulb:
Both the doctor and the front office staff should be able to schedule a follow-up visit. Patients should be notified of follow-ups. The notification system must take the local circumstances into account. Is a paper slip required? An SMS? A WhatsApp notification? Notification services of any kind, digital or physical, add variable cost.  
+++

[^1]: An OGTT, or oral glucose tolerance test, is performed 2 hours after ingesting 75 g of glucose.
