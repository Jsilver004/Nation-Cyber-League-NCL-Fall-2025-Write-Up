# Network Traffic Analysis

## Objective

Analyze captured network traffic to identify malicious infrastructure, DNS activity, and network indicators of compromise (IOCs).

## Skills Demonstrated

- Wireshark packet inspection
- DNS traffic analysis
- HTTP inspection
- TLS analysis
- IOC identification
- Network investigation

## Tools
- Wireshark

## Methodology

## Problem 1:

### Step 1 - Identify the DNS Server

The packet capture was examined to determine which host was responding to DNS requests. By following the DNS query and response traffic the DNS server was identified based on its communication pattern.

(SS. Inspection)

### Step 2 - Investigate DNS Queries

After identifying the DNS server, DNS requests were reviewed for unusual or suspicious domains. One domain stood out from normal traffic and appeared to be associated with a potentially malicious software installation.

(SS)

### Step 3 - Analyze DNS Response

The DNS response records were inspected to determine the destination IP address associated with the suspicious domain. Additonal DNS record information helped verify the service being used.

(SS)


## Takeaways

- DNS traffic often provided early indicators of malicious activity
- Filtering DNS queries can quickly reveal suspicious infrastucture
- Corrrelating DNS requests with responses helps identify attacker-controlled resources
- Packet analysis is a fundamental skill for threat hunting
