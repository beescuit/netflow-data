# Netflow Data Resources

This repository aggregates publicly available resources related to the collection, sale, and implications of netflow data.

"Netflow data" refers to metadata about network traffic. Usually, it contains source/destination IPs, ports, protocols, timestamps and packet counts of internet connections [(source)](https://www.team-cymru.com/netflow). While it (allegedly) does not include the contents of the traffic itself, this metadata can still reveal detailed patterns of online behavior.

Over the past decade, data brokers such as [Team Cymru](https://www.team-cymru.com/) have collected netflow data from numerous Internet Service Providers (ISPs) around the world. Access to this data is then sold to private companies and government agencies in the name of "threat intelligence".

## Why?

Access to netflow data poses significant risk to internet privacy. By analyzing patterns in timing, frequency, and destination of connections, adversaries can perform correlation attacks that can aid in identifying users behind VPNs or Tor and tracking their activity online—potentially enabling mass surveillance. The limited amount of public information around this topic allows such companies to operate in a legal "gray zone", where much of the data is collected without informed consent from the end users.

Team Cymru calls the claims above "statistically inaccurate", [arguing](https://www.team-cymru.com/post/team-cymru-myth-vs-fact) that their service "enables the mapping of malicious devices, not people." They say netflow data can’t track individuals because many websites use CDNs and shared infrastructure, making it "impossible" to identify visited sites. Of course, their view is biased: many sites aren’t behind CDNs and remain identifiable by IP. Plus, from a netflow perspective, legitimate users are often indistinguishable from malicious actors. How do you tell the difference between a ransomware operator SSH'ing into a C2 server through a VPN and a journalist doing the same to update their personal blog?

## Data Brokers

### Team Cymru

[Team Cymru](https://www.team-cymru.com/) is the most known aggregator/broker of netflow data. They sell access to such data through the ["Pure Signal Recon" platform](https://www.team-cymru.com/cyber-threat-hunting-tools), previously known as "Augury".

#### Data Sources

The data collected by Team Cymru comes from "Partner ISPs", likely through its [Nimbus Threat Monitor](https://www.team-cymru.com/nimbus-threat-monitor) product, a "no-cost" platform that "cross-references your network flows" with their IP Reputation database for threat detection. Since this product ingests netflow data, it's highly likely that it's the source of most of the data in their "data ocean".

#### Coverage

The extent of the netflow logs collected by Team Cymru is not very clear, but it probably hovers around 90-100% of all internet traffic. [This article](https://www.vice.com/en/article/us-military-bought-mass-monitoring-augury-team-cymru-browsing-email-data/) by Vice published in 2022 cites [this now deleted webpage](https://archive.is/3YQlc#selection-1297.32-1297.52), which claimed that Augury had "visibilty into 93% of internet traffic". [Their website](https://www.team-cymru.com/aboutpuresignal) claims that they help protect 142+ CSIRTs, "representing approximately 52% of IPV4 and 75% of IPV6".

#### Clients

Team Cymru sells access to their Pure Signal platform to private companies and government agencies. They [claim](https://www.team-cymru.com/post/team-cymru-myth-vs-fact) that the platforms are identical and no additional access is provided to government clients.

U.S. Government Agencies:

- **U.S. Navy**: [This procurement record](https://sam.gov/opp/96b4874e76af45be90bb5a0b8b2bdb6b/view) shows that the has purchased access to the platform in the past ([Vice](https://www.vice.com/en/article/us-military-bought-mass-monitoring-augury-team-cymru-browsing-email-data/)).
- **Naval Criminal Investigative Service (NCIS)**: [This complaint letter](https://www.documentcloud.org/documents/22670252-1763_001/) points out that this agency has purchased and used netflow data from Team Cymru ([Vice](https://www.vice.com/en/article/us-military-bought-mass-monitoring-augury-team-cymru-browsing-email-data/)).
- **FBI**: In 2023, Vice published [an article](https://www.vice.com/en/article/fbi-bought-netflow-data-team-cymru-contract/), along with [one of FBI's contracts](https://www.documentcloud.org/documents/23722785-fbi-team-cymru/) with Team Cymru, specifically for it's "Cyber Division", which investigates cybercrime.
- **Secret Service**: [Vice](https://www.vice.com/en/article/us-military-bought-mass-monitoring-augury-team-cymru-browsing-email-data/): "Although they don’t explicitly mention Augury, Motherboard found multiple contracts between Argonne Ridge Group and the FBI and Secret Service."
- **IRS**: In 2023, Vice published [an article](https://www.vice.com/en/article/irs-wants-to-buy-internet-mass-monitoring-tool-team-cymru-netflow/) with references to [this procurement document](https://sam.gov/opp/b7edba382c88455ba48a432c5a911da7/view), in which the IRS seeked to obtain a subscription on Team Cymru's platform.
- **Defence Counterintelligence and Security Agency (DCSA)**: [404media](https://archive.is/FatPu): "the DSS lays out what it believes is one alternative to buying access to Augury—placing sensors across the world to collect such data itself." ([document](https://www.documentcloud.org/documents/23991392-dssdcsa-on-team-cymru-netflow/)).
- **Defense Threat Reduction Agency (DTRA)**: [404media](https://archive.is/XqxqD): "the Defense Threat Reduction Agency (DTRA) says it is using the data to perform vulnerability assessments of U.S. and allied systems.".

## Articles referencing Netflow Data

This section contains threat intelligence articles that reference the use of Netflow Data for investigation.

- [Recorded Future - North Korea’s Ruling Elite Are Not Isolated](https://www.recordedfuture.com/research/north-korea-internet-activity)
- [Recorded Future - Malicious Android Applications Raise Concerns for Enterprises](https://www.recordedfuture.com/blog/malicious-android-apps)
- [SecurityScorecard - Operation Phantom Circuit: North Korea’s Global Data Exfiltration Campaign](https://securityscorecard.com/blog/operation-phantom-circuit-north-koreas-global-data-exfiltration-campaign/)
- [Citizenlab - Hooking Candiru](https://citizenlab.ca/2021/07/hooking-candiru-another-mercenary-spyware-vendor-comes-into-focus/)
- [Sekoia - Raspberry Robin’s botnet second life](https://blog.sekoia.io/raspberry-robins-botnet-second-life/)
- [Silent Push - Raspberry Robin: Copy Shop USB Worm Evolves to Initial Access Broker Enabling Other Threat Actor Attacks](https://www.silentpush.com/blog/raspberry-robin/)
- [Silent Push - FIN7: Silent Push unearths the largest group of FIN7 domains ever discovered](https://www.silentpush.com/blog/fin7/)
- [Proofpoint - Latrodectus: This Spider Bytes Like Ice](https://www.proofpoint.com/us/blog/threat-insight/latrodectus-spider-bytes-ice)
- [Dragos: Lessons Learned from Telemetry Analysis of DarkSide Affiliate Exfiltration Operations](https://www.dragos.com/blog/industry-news/lessons-learned-from-telemetry-analysis-of-darkside-affiliate-exfiltration-operations/)

## Countermeasures

- [Mullvad: DAITA](https://mullvad.net/en/blog/introducing-defense-against-ai-guided-traffic-analysis-daita)

## ISPs that share Netflow Data

This section is a list of ISPs suspected of sharing Netflow data with companies like Team Cymru. This list might be innacurate. It is the result of assumptions made based off of public records, for which the thought processes are described under each entry.

### AS46844 - Sharktech

[The Phantom Circuit Report](https://securityscorecard.com/blog/operation-phantom-circuit-north-koreas-global-data-exfiltration-campaign/) by Recorded Future details a timing analysis used to deanonymize connections between North Korean IP addresses and C2 servers hosted by "Stark Industries". The connections were made through Astrill VPN and "Oculus Proxies" tunnels.

Looking at the connections between North Korean IPs and Astrill VPN servers, we can assume that the AS that is uploading netflow data to Cymru is the company behind the infrastructure for the VPN servers, as NK is obviously not a Cymru client. The VPN ips listed in the report are `70.39.70.196, 204.188.233.68, 45.58.143.196, 70.39.70.197, and 199.115.99.62`. All of these IPs are owned by AS46844/Sharktech.

Sharktech is also fairly public about their relationship with Team Cymru. [Here's a linkedin post](https://www.linkedin.com/pulse/sharktech-dns-amplification-ddos-attack-tim-timrawi-vq9dc/) from their CEO about how they reached out to Cymru back in 2005.

[This report](https://www.recordedfuture.com/research/north-korea-internet-activity) also refereces North Koreans connecting to Sharknet servers.

### AS44477 - STARK INDUSTRIES SOLUTIONS LTD

[This report on the FIN7 Campaign](https://www.team-cymru.com/post/fin7-the-truth-doesn-t-need-to-be-so-stark) by Team Cymru states: "we have been working directly with Stark for several months to assist in their objective of identifying and reducing abuse activity on their networks".

[Stark's Website](https://pq.hosting/en/news/751-nimbus-threat-monitor-new-protection-for-pqhosting-clients.html) explicitly mentions that they are a Nimbus Threat Monitor client.

[The Phantom Circuit Report](https://securityscorecard.com/blog/operation-phantom-circuit-north-koreas-global-data-exfiltration-campaign/) by Recorded Future mentions Stark Industries and includes netflow data to and from their servers.

### AS31549 - Aria Shatel PJSC

[The Malicious Android Applications](https://www.recordedfuture.com/blog/malicious-android-apps) report by Recorded Future mentions observed traffic between Aria Shatel Company and IP addresses owned by Telegram (AS62041). It also mentions communication with IPs owned by "XTIDC", a chinese company. XTIDC's range has apparently been transfered to Sharktech. Assuming Telegram and XTIDC were not sharing data with Cymru, we can guess Aria Shatel is.