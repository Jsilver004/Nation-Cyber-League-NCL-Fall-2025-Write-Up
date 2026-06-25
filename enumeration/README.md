# Enumeration

## Objective 

Analyze structure network telemetry to identify indiators of compromise (IOCs), attacker infrastructure, and trough systematic data enumeration.

## Skills Demonstrated
- JSON parsing
- Threat hunting
- DNS analysis
- TLS certificate analysis
- IOC extraction
- Linux command line

## Tools
- jq
- sort
- head
- Kali Linux

## Methodology

## Problem 1

### Step 1 - Analyze Network Telemetry

Network event data stored in JSON format was examined using the 'jq' command-line utility. Relevant fields were extracted to identify suspicious activity and reduce the amount of data requiring manual inspection.

