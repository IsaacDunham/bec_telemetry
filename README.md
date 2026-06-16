# About
This repository contains sample logs including a small amount of benign activity as well as a business email compromise that occurred via device code phishing. 

Note: This data is from a non-production lab environment, and most identifiers and GUIDs (except most non-private values, like client APP IDs) were anonymized. Anoynmizations were, as much as possible, performed on a 1:1 static mapping basis, meaning any expected joins ought still work, though this anonymization will likely explain any discrepancies in how you might expect the telemetry to look.

To generate this telemetry, I...
1. Did some benign actions - reading email, sending email, sending a Teams message from my normal IP address, shown as 192.168.1.1 in the logs.
2. Set up a modified version of [SquarePhish2](https://github.com/nromsdahl/squarephish2) to device code phish myself from a separate system and IP address. It was configured to automatically register a device and retrieve a PRT. 
3. After falling for my own phish, I, as the adversary, performed activity from IP address 10.0.0.1 and 10.0.0.2. This included 
  1. registering a device with which to retrieve a PRT
  2. accessing Microsoft Office on Google Chrome via [x-ms-RefreshTokenCredential](https://specterops.io/blog/2025/04/07/an-operators-guide-to-device-joined-hosts-and-the-prt-cookie/?source=rss----f05f8696e3cc---4#:~:text=RefreshTokenCredential)
  3. Creating mailbox forwarding and hiding rules in-line with what is commonly observed in business email compromise.