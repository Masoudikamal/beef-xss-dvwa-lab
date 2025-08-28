# BeEF + XSS mot DVWA — lab

## Prosjektpresentasjon
I et lukket, fiktivt labmiljø demonstrerte jeg hvordan en refleksiv XSS i DVWA kan brukes til å “hooke” en nettleser med **BeEF**, slik at klienten vises og kan inspiseres i BeEF-panelet.

> **Etikk:** Dette er kun en lab/demo. Ikke gjennomfør mot systemer du ikke eier eller har eksplisitt tillatelse til.

### Mål
- Vise at en XSS-sårbarhet kan gi BeEF-hook (offer dukker opp i BeEF)
- Dokumentere at BeEF leser klientinfo (origin, cookies, hostname) i UI

### Miljø
- Angriper: Kali Linux med **BeEF**
- Mål: **DVWA** (XSS: Reflected; lav sikkerhetsnivå)
- Offer: Nettleser i samme labnett

### Fremgang (høydenivå) m/ evidens
**1) BeEF kjører (hook-server tilgjengelig)**  
*Skjermbilde som viser at BeEF er startet og lytter.*  
![BeEF start](images/beef-start.png)

**2) XSS-injeksjon i DVWA**  
*Skjermbilde av DVWA der payload legges inn i XSS-feltet (eventuelle URL/IP-er kan sladdes).*  
![DVWA XSS-injection](images/dvwa-inject.png)

**3) Offer “hooked” i BeEF**  
*Skjermbilde av BeEF-UI som viser offerets nettleser i venstre panel.*  
![BeEF victim listed](images/beef-victim-listed.png)

**4) Klientdata i BeEF → Details**  
*Skjermbilde av Details-fanen som viser `origin`, `cookies` og `hostname`. Maskér sensitivt (f.eks. session-ID).*  
![BeEF details](images/beef-details.png)

### Læringspoeng
- Klient-side sårbarheter (XSS) kan gi innsikt/kontroll over offerets nettleser.
- “Synlige” effekter i BeEF-UI gjør risikoen enkel å forstå for ikke-tekniske lesere.
- Forsvar: inndata-validering/escaping, **CSP**, `HttpOnly`/`Secure`-cookies, oppdaterte rammeverk, sikkerhetstester i pipeline.

## Lisens
MIT
