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

### AS28186 - ITS TELECOMUNICACOES LTDA (and AS263880, AS262373, AS263636, AS263151)

Team Cymru's Nimbus webpage contains a testimonial made by `Francisco Badaró, Telecommunications and Training Manager, ITS Brasil`.

Francisco has also published documents on the usage of Nimbus:
- https://www.lacnic.net/innovaportal/file/5959/1/ftl-lacnic-37-vfinal.pdf (Portuguese);
- [Practical ISP CSIRT Incident Handling with NIMBUS from Team Cymru](https://www.researchgate.net/publication/354849906_Practical_ISP_CSIRT_Incident_Handling_with_NIMBUS_from_Team_Cymru_How_to_leverage_network_flows_ELK_Stack)

The publication in english contains a screenshot of the Nimbus dashboard that outlines communications with a Mirai botnet IP (89.187.171.77). The IPs on the other side of the connection are:

```
- 187.44.188.254 (AS28186 - ITS TELECOMUNICACOES LTDA )
- 168.205.36.135 (AS263880 - WANTEL TECNOLOGIA LTDA. ­ EPP)
- 168.195.252.190 (AS262373 - CONECT TELECOM)
- 177.200.117.84 (AS263636 - CALLNET TELECOM)
- 191.242.177.14 (AS263151 - CONECT TELECOM)
- 187.44.193.90 (AS28186 - ITS TELECOMUNICACOES LTDA)
```

### Other ASes

The documentation for Team Cymru's "Scout Ultimate" product is publicly available online: https://scout.cymru.com/docs/scout/ultimate. It includes sample response data from a request to `GET /api/scout/ip/{ip}/details`, looking up the `104.18.213.12` IP, belonging to Cloudflare. As Cloudflare does not share netflow data with Team Cymru, it is safe to assume that every peer in the response of this request does share netflow logs with them. By parsing the response data, we get the following results:

```
206476 - IPTECHNOLOGY, IT
19556 - ISOTECH-INC, US
15038 - CAMBINC-1, US
32244 - LIQUIDWEB, US
17625 - BLAZENET-IN-AP BlazeNets Network, IN
328350 - NetworkComputing-AS, ZA
25512 - CDT-AS The Czech Republic, CZ
36511 - NETDT-GUA, GP
559 - SWITCH Peering requests: peering@switch.ch, CH
43507 - RETE-AS, CZ
37199 - VANILLA, ZA
37406 - RCS, SS
60304 - STARNET, AL
25145 - AS-TEKNOTEL Teknotel Telekomunikasyon A.S., TR
201814 - MEVSPACE, PL
265727 - Infinite Wireless & Networking, BZ
141723 - BEEONLINE-AS-AP BEE ONLINE, BD
142453 - FASTJET-AS-IN FASTJET TELECOM PRIVATE LIMITED, IN
38477 - SOLARIX-NZ Solarix Networks Limited, NZ
50782 - COSYS, AT
23955 - TASHICELL-DOMESTIC-AS Tashi InfoComm Limited, BT
199468 - SOLWAY-COMMS-UK, GB
328212 - The-University-Of-Cape-Coast-AS, GH
51524 - ASNETDELUXE, CZ
45942 - SIKKANET-AS-AP Sikka Broadband Pvt. Ltd., IN
61681 - MEGANET BRASIL, BR
132971 - SIKKASTAR-AS-IN Sikka Star powered by Sikka Broadband, IN
328633 - MikroTikSA-Networks, ZA
20545 - GRENA-AS Tbilisi, Georgia, GE
38203 - ADNTELECOMLTD-BD ADN Telecom Ltd., BD
3582 - UONET, US
25021 - CIEF-AS Etat de Fribourg, SITel, CH
134351 - LEASEWEB-AS-AP Leaseweb Japan K.K., JP
149058 - SPEEDLINKS-AS-AP Speed Links, BD
137412 - TASHICELL-MOBILE-AS Tashicell Domestic AS Thimphu Bhutan, BT
197207 - MCCI-AS, IR
36866 - JTL, KE
132547 - SAJAGPRAHARI-AS Sajag Prahari Foundation, IN
132519 - SIKKACABLE-AS-IN Sikka Cable, IN
23916 - HOTHL-NZ House of Travel Holdings Ltd, NZ
766 - REDIRIS RedIRIS Autonomous System, ES
266068 - Tribunal de Justica do Estado de Sergipe, BR
200521 - SEAP-AGE, ES
52420 - Intercom SRL, AR
51167 - CONTABO, DE
197550 - ASINET4YOU, CZ
23838 - SOLARIX-INTERNET-AS-AP Solarix Networks Limited, NZ
38437 - WIC-AS-NZ Wicked Networks, NZ
5379 - MK-UKIM-1, MK
197698 - DHT_SYSTEMS, CZ
39235 - DAT-AS cz.dat autonomous system, CZ
61510 - Cooperativa Telefonica de Calafate Ltda., AR
11878 - TZULO, US
14061 - DIGITALOCEAN-ASN, US
13041 - CESCA-AC, ES
9009 - M247, RO
263812 - SONDATECH S.A.S., AR
29611 - ELITE-AS, GB
206804 - ESTNOC-GLOBAL, EE
16276 - OVH, FR
49770 - INTERNETPORT-AS, SE
1213 - HEANET, IE
268829 - ZUTTEL FIBRA LTDA, BR
12874 - FASTWEB, IT
262401 - GSTN TELECOMUNICACOES LTDA, BR
19994 - RACKSPACE, US
4270 - Red de Interconexion Universitaria, AR
31122 - DIGIWEB-AS, IE
197829 - GOBIERNO-DE-NAVARRA, ES
9050 - RTD Bucharest, Romania, RO
208046 - COLOCATIONX-DATACENTER Dedicated Server Provider, GB
24309 - CABLELITE-AS-AP Atria Convergence Technologies Pvt. Ltd. Broadband Internet Service Provider INDIA, IN
270786 - CITYNET COM. DE PROD. DE INFORMATICA LTDA, BR
269996 - HENDERSON.NET SRL, AR
266062 - R2 DADOS LTDA - ME, BR
41354 - ITS-TG, GB
4770 - ICONZ-AS ICONZ Ltd, NZ
22245 - WICHITA-STATE-U, US
60404 - LITESERVER, NL
17913 - GIPLNET-AP Guj Info Petro Limited, IN
56055 - MLS-NC Micro Logic Systems, NC
15488 - UPV-EHU, ES
328114 - Comsol-Networks-AS, ZA
56450 - ALBERON_AS, CZ
31103 - KEYWEB-AS, DE
46844 - SHARKTECH, US
135328 - TSL-AS-AP Tangelo Services, NZ
55256 - NETSKOPE, US
25543 - FasoNet-AS, BF
10139 - SMARTBRO-PH-AP Smart Broadband, Inc., PH
45773 - HECPERN-AS-PK PERN AS Content Servie Provider, Islamabad, Pakistan, PK
37020 - CELTEL-DRC, CD
32111 - CITIGROUP-JAPAN, US
140443 - IDNIC-HERZA-AS-ID PT Herza Digital Indonesia, ID
9299 - IPG-AS-AP Philippine Long Distance Telephone Company, PH
266168 - TOPNET-MS LTDA - ME, BR
37340 - Spectranet, NG
27357 - RACKSPACE, US
15630 - UNED UNED Autonomous System, ES
34285 - JJAA-AS, ES
328943 - AAS1-AS, AO
28586 - BANCO BRADESCO SA, BR
37447 - ORANGE-RDC, CD
17676 - GIGAINFRA SoftBank Corp., JP
36884 - MAROCCONNECT, MA
198096 - CICA Centro Informatico Cientifico de Andalucia - CICA, ES
263612 - IP CARRIER BRASIL, BR
262659 - ULTRAWAVE TELECOM, BR
27446 - AS-ERCBB, US
53187 - UNIVERSIDADE ESTADUAL DE CAMPINAS, BR
43424 - MAGICRETAIL, FR
52798 - BANCO BTG PACTUAL S.A., BR
8452 - TE-AS TE-AS, EG
53070 - T-Systems do Brasil Ltda., BR
268234 - VNTFMAIS LTDA, BR
28360 - WKVE Asses. em Servicos de Inform. e Telecom. Ltda, BR
264738 - Sebastian Souto SSSERVICIOS, AR
21826 - Corporacion Telemic C.A., VE
17471 - CYBERNET-BD-AS Grameen Cybernet Ltd. Bangladesh. AS for local peering and transit. Dhaka, BD
264417 - Megalink Telecom, BR
37371 - HORMUUD, SO
16135 - TURKCELL-AS Turkcell A.S., TR
```