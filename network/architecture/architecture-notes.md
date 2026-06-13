## Current State

The environment consists of domain-joined Windows hosts communicating with an internal Active Directory domain controller and external Internet resources. During triage, host 10.11.11.203 accessed acjabogados.com and downloaded /40group.tiff over HTTP, indicating insufficient outbound traffic controls.

## Risks Identified

- Direct outbound HTTP access
- Lack of inspection controls
- Potential malware download
- Limited monitoring visibility

## Recommended Future State

Implement a defense-in-depth architecture including a next-generation firewall, web proxy, IDS/IPS, SIEM, and network segmentation. These controls improve visibility, reduce attack surface, and help detect malicious communications such as command-and-control traffic and malware delivery.
