# Home-Network-Hardening

This project documents a security assessment and hardening of a personal home network. The objective was to identify connected devices, enumerate exposed network services, review router security settings and apply security improvements based on industry best practices. The assessment was conducted in a controlled environment on my own home network.



## Objectives

*    Discover all devices connected to the network
*    Identify exposed services on the router
*    Review router security configuration
*    Harden insecure settings
*    Document findings and remediation
*    Produce a professional security assessment


##  **Network Topology**

                                                                             Internet
                                                                                 │
                                                                          Jio Fiber Router
                                                                                 │
                                                                  ┌────────┬────────┬────────┬
                                                                  │        │        │        │
                                                               Kali Linux  Samsung  Samsung  Samsung
                                                                Laptop      Phone    Phone    Phone

## Tools used

                                                        | Tool                   | Purpose              |
                                                        | ---------------------- | -------------------- |
                                                        | Kali Linux             | Security Testing     |
                                                        | Nmap                   | Port Scanning        |
                                                        | arp-scan               | Device Discovery     |
                                                        | Jio Router Admin Panel | Configuration Review |


## **Phase 1 — Network Discovery**

ARP Scan

Command : sudo arp-scan --localnet

 ## Devices Discovered

                                                        | IP Address     | Device        |
                                                        | -------------- | ------------- |
                                                        | 192.168.29.1   | Jio Router    |
                                                        | 192.168.29.141 | Kali Laptop   |
                                                        | 192.168.29.115 | Samsung Phone |
                                                        | 192.168.29.181 | Samsung Phone |
                                                        | 192.168.29.222 | Samsung Phone |

## Phase 2 — Router Enumeration

Command : sudo nmap -A 192.168.29.1

## Open Ports

                                                        | Port | Service | Status |
                                                        | ---- | ------- | ------ |
                                                        | 53   | DNS     | Open   |
                                                        | 80   | HTTP    | Open   |
                                                        | 443  | HTTPS   | Open   |
                                                        | 1900 | UPnP    | Open   |
                                                        | 7443 | HTTPS   | Open   |
                                                        | 8080 | HTTP    | Open   |
                                                        | 8443 | HTTPS   | Open   |

## Phase 3 — Router Security Review

The router configuration was manually inspected using the administrative interface.

## Wireless

                                                        | Setting        | Value    |
                                                        | -------------- | -------- |
                                                        | Security       | WPA2-PSK |
                                                        | Encryption     | CCMP     |
                                                        | SSID Broadcast | Enabled  |
                                                        | Channel Width  | 20 MHz   |


## Firewall

### Firewall protections 

  enabled:
  
    * TCP SYN Protection
    * Smurf Protection
    * Ping of Death Protection
    * Fraggle Protection
    * DNS Amplification Protection
    
   Disabled:
   
    * ICMP Response on WAN


## Web Management
                                                        | Setting                     | Status   |
                                                        | --------------------------- | -------- |
                                                        | Local Management over Wi-Fi | Disabled |

## Port Forwarding

   No custom rules configured.

## Media Server

  Disabled

## Remote Access

  No remote management rules identified.

## Phase 4 — Hardening Actions

  The following improvements were applied during the assessment.
  
                                                        | Action                                | Status    |
                                                        | ------------------------------------- | --------- |
                                                        | Changed router administrator password | Completed |
                                                        | Verified firewall protections         | Completed |
                                                        | Verified no port forwarding rules     | Completed |
                                                        | Verified media server disabled        | Completed |
                                                        | Verified WAN ping disabled            | Completed |
                                                        | Reviewed wireless security            | Completed |

## Findings
### Positive Findings
*    Strong WPA2 encryption enabled
*    No exposed SSH service
*    Firewall protections enabled
*    No unnecessary port forwarding
*    Media server disabled
*    Local management restricted
  
### Potential Improvements
*  Upgrade to WPA3 if supported
*  Disable UPnP if not required
*  Regular firmware updates
*  Use strong administrator passwords
*  Periodically review connected devices
  
## Lessons Learned

During this project I learned how to:

*  Discover hosts using ARP scanning
*  Enumerate router services using Nmap
*  Interpret common network services
*  Review router security settings
*  Perform basic network hardening
*  Document security findings professionally

  ## Disclaimer

  This assessment was conducted only against devices that I own and manage. No unauthorized systems were accessed or tested.
