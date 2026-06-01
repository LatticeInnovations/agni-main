---
order: 110
---

# Offline-first design
Public health systems have a tiered structure — beginning with home care, followed by community, primary, and secondary+ care. The more distributed the tier, the more interruptions it faces while accessing the internet.

Therefore, a system that supports community and primary care tiers has to be offline-first, by design. Agni achieves this through a two-way synchronization (sync) process, illustrated below.

![Agni's two-way sync](/images/Agni-sync.png)

Sync operates in the background, on a 15-minute schedule. As and when the network is available, 2-way incremental sync takes place—the mobile app sends new and updated data to the server, and the server does the same.

The app always initiates a sync. This reduces the likelihood of concurrent requests, leveling the demand placed on on the server.
