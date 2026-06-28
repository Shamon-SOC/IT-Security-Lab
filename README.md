# IT Security Lab – SOC Analysis
Det här är min samling av labb för att visa mina färdigheter inom:
- Nätverksanalys (Wireshark)
- Logganalys (Splunk)
- Incidentrapportering
- SOC-arbetsflöden (TryHackMe)
## Labb
- [Nätverksanalys med Wireshark](./Labb-1-Wireshark/)
- [Logganalys med Splunk](./Labb-2-Splunk/)
- [TryHackMe – SOC Level 1](./Labb-3-TryHackMe/)
- [Incidentrapport – Blue Team Labs](./Labb-4-Incidentrapport/)
## Verktyg
- Wireshark
- Splunk Free
- TryHackMe
- Blue Team Labs Online
## Certifieringar (pågående)
- TryHackMe Cyber Security 101 ✅
- TryHackMe SOC Level 1 – pågående
# Labb 1 – Nätverksanalys med Wireshark
## Verktyg
- Wireshark
## PCAP-fil
2025-01-22-traffic-analysis-exercise.pcap
## Filter använda
- http
- dns
- ip.addr == 10.1.17.215
## Fynd
### Fynd 1 – Misstänkt PowerShell-script
- Filter: http
- En .ps1-fil laddades ner via HTTP
- PowerShell-scripts används av hackare för att köra skadlig kod
- ### Fynd 2 – Misstänkt domän
- Filter: dns
- Datorn kontaktade wpad.bluemoontuesday.com
- Okänd domän – trolig C2-server (Command & Control)
- Svar: "No such name" – domänen finns inte
### Fynd 3 – Infekterad dator identifierad
- Filter: ip.addr == 10.1.17.215
- Datorns namn: BLUEMOONTUESDAY
- IP-adress: 10.1.17.215
### Fynd 4 – Extern kommunikation
- Datorn kommunicerade med extern server
- Extern IP: 23.220.102.9
- Protokoll: HTTP
## Slutsats
Datorn BLUEMOONTUESDAY (10.1.17.215) var infekterad.
Den laddade ner ett misstänkt PowerShell-script och
kommunicerade med externa servrar – troliga tecken på malware-infektion.
# Labb 3 – TryHackMe SOC Level 1
## Plattform
TryHackMe.com
## Slutförda rum
### Offensive Security Intro ✅
- Lärde mig tänka som en angripare
- Använde dirb för att hitta dolda sidor
- Hittade dold admin-sida på FakeBank
### Defensive Security Intro ✅
- Jobbade i ett simulerat SOC
- Analyserade säkerhetslarm
- Eskalerade incident till SOC Team Lead
- Blockerade misstänkt IP i firewall
### Junior Security Analyst Intro ✅
- Analyserade SIEM-dashboard
- Identifierade misstänkt IP: 221.181.185.159
- Blockerade IP i firewall
- Eskalerade till Will Griffin (SOC Team Lead)
### SOC Role in Blue Team ✅
- Lärde mig roller i ett SOC-team
- Blue Team vs Red Team
- CISO, SOC Manager, SOC Analyst
## Status
TryHackMe SOC Level 1 – pågående
# Labb 4 – Incidentrapport
## Scenario
Simulerad SOC-incident från Blue Team Labs Online
## Summary
En brute force-attack identifierades mot FakeBanks system.
Angriparen försökte logga in via SSH med upprepade försök.
## Timeline
- 21:11 – Unauthorized login attempts från IP 221.181.185.159 till port 22
- 21:15 – Successful SSH login från misstänkt IP detekterades
- 21:15 – SOC-analytiker notifierades via SIEM-larm
- 21:20 – IP-adress blockerades i firewall
- 21:25 – Incident eskalerades till SOC Team Lead (Will Griffin)
## IOCs (Indicators of Compromise)
- Misstänkt IP: 221.181.185.159
- Attacktyp: Brute Force SSH
- Målsystem: FW-NY-01
## Åtgärder
- IP blockerad i perimeter firewall
- Incident eskalerad till SOC Team Lead
- Konto flaggat för vidare utredning
## Slutsats
Incidenten detekterades och hanterades via SIEM-dashboard.
Angriparen blockerades inom 10 minuter från första larmet.
