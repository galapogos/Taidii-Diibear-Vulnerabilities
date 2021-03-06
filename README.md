# Taidii-Diibear-Vulnerabilities
Author: <ins>Goi</ins> Si Han

This repository describes 3 vulnerabilities that were discovered in the Taidii Diibear Android application v2.4.0 and all its derivatives (com.taidii.diibear.\*). While not tested on other versions, the vulnerability likely exists in versions 2.4.0 and lower.

The vulnerability was responsibly disclosed to Taidii, who has acknowledged and remediated the vulnerabilities in v2.5.0. The vulnerabilities were filed as CVE-2020-35454, CVE-2020-35455 and CVE-2020-35456 after responsible disclosure to Taidii.

### Vulnerability disclosure timeline
25 Nov 2020 - Emailed service@taidii.com to request for appropriate contact for vulnerability disclosure, with no response.  
26 Nov 2020 - Emailed taidii.singapore@gmail.com to request for appropriate contact for vulnerability disclosure, with no response.  
01 Dec 2020 - Used the in-app feedback form of MindChamps Android app (which uses Taidii Diibear) to request for appropriate contact for vulnerability disclosure, with no response.  
07 Dec 2020 - Contacted MindChamps centre director to request for appropriate Taidii contact for vulnerability disclosure, with acknowledgement.  
09 Dec 2020 - Contacted CEO of Taidii (Bin Wang) on Linked to request for appropriate contact for vulnerability disclosure, with no response.  
09 Dec 2020 - MindChamps CIO requested for details of vulnerabilities, report provided.  
15 Dec 2020 - Reserved CVE IDs CVE-2020-35454, CVE-2020-35455 and CVE-2020-35456..  
22 Dec 2020 - Requested for status update from MindChamps.  
23 Dec 2020 - MindChamps confirmed that both Taidii is verifying the vulnerabilities, and making the necessary fixes.  
22 Jan 2021 - Requested for status update from MindChamps, with no response.  
27 Jan 2021 - Reported vulnerabilities to SingCERT.  
24 Feb 2021 - Linked up with Taidii via SingCERT to provide details.  
05 Mar 2021 - All 3 vulnerabilities fixed in Taidii Diibear and all derivatives on Google Play store.  
15 Mar  2021 - Updated CVE with vulnerability details.  

### Taidii Diibear description
Taidii Diibear (com.taidii.diibear) is an integrated teacher-parent communication platform that provides the following features (as stated on the Taidii website):  
- Ensures private communication between teachers and parents  
- Biometric security ensuring safety and security of child  
- CLOUD based application always ensures accessible information  
- Communicates information to parents in real-time  

Taidii Diibear is used by several childcare facilities (com.taidii.diibear.\*) which, as of vulnerability disclosure date, has tens of thousands of installs according to Google Play  

### CVE-2020-35454  
The application was configured to have Android backup enabled. This resulted in two instances of sensitive data disclosure where plaintext sensitive data was included in the Android generated backup.  
First, it was discovered that the application stores sensitive data in plaintext within the Shared Preferences, thereby disclosing the following sensitive information in plaintext:  
- User credentials (username and password)
- Authentication token
- Center ID
- Medication information  

In addition, it was discovered that the application stores sensitive data in plaintext within the sqlite database, thereby disclosing the following sensitive information in plaintext:  
- Student profile picture
- Personal data such as birth region, center type, date of birth, enter date, full name, gender, leave data, local index, nickname, registration number, and school count  

An attacker with physical access to the device and no prior access to the app can access this sensitive data via Android backup, and use it to gain full access to the victim???s account, thereby resulting in a full compromise of the account.  

**CVSS 3.1 Scoring**: 6.8 (CVSS:3.1/AV:P/AC:L/PR:N/UI:N/S:U/C:H/I:H/A:H)

### CVE-2020-35455  
Two instances of insecure data storage were discovered.  
First, it was discovered that the application stores sensitive data in plaintext within the Shared Preferences, thereby disclosing the following sensitive information in plaintext:  
- User credentials (username and password)  
- Authentication token  
- Center ID  
- Medication information  

In addition, it was discovered that the application stores sensitive data in plaintext within the sqlite database, thereby disclosing the following sensitive information in plaintext:  
- Student profile picture  
- Personal data such as birth region, center type, date of birth, enter date, full name, gender, leave data, local index, nickname, registration number, and school count  

An attacker with local read/write access to the device and no prior access to the app can access this sensitive data, and use it to gain full access to the victim???s account, thereby resulting in a full compromise of the account.  

**CVSS 3.1 Scoring**: 7.8 (CVSS:3.1/AV:L/AC:L/PR:L/UI:N/S:U/C:H/I:H/A:H)

### CVE-2020-35456  
The application performs excessive logging, thereby disclosing private chat messages in plaintext. This includes publicly accessible links to private media files such as images and PDF documents.
These application logs are readily accessible by an attacker with local access to the device, and the private chat messages were revealed when the victim navigates to the ???Message??? activity.

**CVSS 3.1 Scoring**: 5.5 (CVSS:3.1/AV:L/AC:L/PR:N/UI:R/S:U/C:H/I:N/A:N)
