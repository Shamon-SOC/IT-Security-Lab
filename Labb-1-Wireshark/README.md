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
### Fynd 2 – Misstänkt domän
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
kommunicerade med externa servrar – troliga tecken på malware-infektion
