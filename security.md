# 4.3 Security

## 4.3 Security overview
The unit template and a likelihood-impact approach to risk prioritisation and mitigation justification were used to complete a mini cyber security risk assessment of the Truelec network. This is in accordance with NIST guidelines that risk assessment evaluates threat and vulnerabilities and estimates likelihood and impact to make decisions on treatment (NIST SP 800-30: https://csrc.nist.gov/pubs/sp/800/30/r1/final).

## 4.3.1 Mini cyber security risk assessment

### 4.3.1.1 Method and scoring
The identification of assets, mapping of the relevant threats/vulnerabilities, the rating of likelihood and impact (Low/Medium/High) and prioritisation of the risks was done using the combined rating (e.g., a matrix).

### 4.3.1.2 Asset inventory (all asset types)

| Asset type | Examples |
|---|---|
| People | ICT admins, HQ/branch staff, contractors |
| Hardware | firewalls, switches/APs, servers, endpoints, CCTV/RFID/IoT |
| Software | booking app, DBMS, OS, firewall/VPN firmware |
| Service | ISP links, site‑to‑site VPN, identity services |
| Data (≥4) | booking DB (PII), HR/payroll, finance, project docs, CCTV/RFID logs |

### 4.3.1.3 Threat coverage (≥8 categories)
Covered categories: phishing/social engineering; malware/ransomware; unauthorised access; insider misuse; misconfiguration; DoS/availability loss; IoT/CCTV compromise; physical theft/damage.

### 4.3.1.4 Completed outputs (evidence)
- Spreadsheet: [risk-assessment-template-v01_completed.xlsx](security/risk-assessment-template-v01_completed.xlsx)  
- TVAMatrix screenshots: link PNG/JPG files stored in `security/` (e.g., `TVAMatrix_1.png`).

### 4.3.1.5 Summary of top risks

| Risk | Asset | L | I | Rating |
|---|---|---|---|---|
| account takeover → data breach | booking DB (PII) | High | High | Very High |
| ransomware → operational outage | endpoints/servers | High | High | Very High |
| payment fraud | finance data | High | High | High |
| lateral movement | firewall/VPN | Medium | High | High |

## 4.3.2 Recommended security controls

### 4.3.2.1 Highest‑risk data asset
The customer booking database (PII) is chosen as the most at risk since being compromised through credentials is very probable, as well as impactful if compromised.

### 4.3.2.2–4.3.2.4 Controls (three) (NIST SP 800-53: https://csrc.nist.gov/pubs/sp/800/53/r5/upd1/final)
1. **IA‑2 (MFA):** Require MFA for VPN and privileged admin access (firewall/server/DB) at the HQ VPN gateway. *Disadvantage:* login friction and recovery overhead.  
2. **AC‑2 (Account management):** Role‑based access, no shared admin accounts, joiner/mover/leaver controls, periodic access reviews. *Disadvantage:* approval overhead for users/ICT.  
3. **SC‑28 (Encryption at rest):** Encrypt DB storage and backups; restrict keys; test restores. *Disadvantage:* key management and recovery testing effort.

### 4.3.2.5 Residual risk
Remaining risk is due to high-order phishing, zero-day carries and WAN failures; other priorities could be monitoring/alerting and tested incident response and recovery.
