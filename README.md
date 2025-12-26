# Troubleshooting-Network-and-Firewall-Issues-Affecting-Oracle-RDS-Connectivity
This project documents a real-world network and firewall troubleshooting scenario affecting Oracle RDS connectivity. The investigation involved client-side testing, AWS network validation, VPN status verification, and cross-account VPC peering configuration.

##  Problem

The client reported failed database connectivity, where application-side network tests (Test-NetConnection) were returning false, indicating a potential network or firewall issue.

Despite the failure on the client side, internal AWS tests initially showed no apparent misconfiguration, requiring deeper investigation.

## 🔍 Investigation Timeline
### 1️⃣ Client-Side Validation

Client reported:

Test-NetConnection returning false

Application unable to reach Oracle RDS endpoint

This indicated a connectivity failure at the network layer.

### 2️⃣ AWS-Side Security Validation

Reviewed Security Group rules:

Inbound rules correctly allowed required ports

Source IP ranges were properly configured

Verified Network ACLs with no blocking rules

No security misconfiguration was found at this stage.

### 3️⃣ Connectivity Testing from AWS

Performed ICMP tests (ping) from internal AWS resources:

Connectivity to the RDS endpoint was successful

Confirmed:

DNS resolution working correctly

No packet loss internally

👉 This confirmed that RDS and AWS networking were healthy.

### 4️⃣ VPN Status Verification

Investigated hybrid connectivity components.

Identified that the site-to-site VPN was in a DOWN state.

This explained:

Client-side Test-NetConnection failures

Successful connectivity only from within AWS

## 🛠 Resolution

Restored VPN connectivity.

Revalidated:

Client-side Test-NetConnection → success

Application database connectivity → restored

Monitored stability post-restoration.

<img width="1086" height="172" alt="image" src="https://github.com/user-attachments/assets/ae59c584-53cd-497b-b7f5-90a75403a0f6" />
