# 4.2 Cloud Services

## 4.2 Cloud Services overview
Truelec operates the booking application on on-premise servers (three at head quarters and one in each branch). The existing servers are nearing the end of life, and the organisation will be faced with the choice of either buying new hardware or shifting the workload to cloud IaaS virtual machines (VMs). This part assesses the ability of cloud VMs to deliver similar capacity, and costs are compared through official provider calculators, whose estimates have been exported to the GitHub repository.

## 4.2.1 Cloud Server

### 4.2.1.1 Scope and assumptions
- **Branches modelled:** 4 → **Total VMs = 3 + 4 = 7**  
- **Usage:** 730 hours/month (always‑on)  
- **OS:** Ubuntu Linux (baseline)  
- **Region basis:** Australian regions (Sydney/Australia East)  
- **Included:** compute + SSD storage  
- **Excluded:** egress, premium support, backups/snapshots (excluded for both providers)

### 4.2.1.2 Baseline VM specification (used for all providers)

| Region basis | OS | vCPU/RAM | Storage | Pricing |
|---|---|---:|---:|---|
| Australia | Ubuntu Linux | 4 vCPU / 16 GB | 384 GB SSD | Pay‑as‑you‑go |

### 4.2.1.3 Provider A estimate — AWS (Amazon EC2)
Sydney; Linux; **m6i.xlarge (4 vCPU/16 GiB)**; **384 GB** EBS; On‑Demand.  
Export: [My Estimate - AWS.csv](cloud/estimates/My%20Estimate%20-%20AWS.csv).  
Monthly: **USD 212.06 ≈ AUD 303.25** (1 USD = 1.43 AUD).

### 4.2.1.4 Provider B estimate — Azure (Virtual Machines)
Australia East; Ubuntu; **D4as v5 (4 vCPU/16 GB)**; **384 GB** SSD managed disks.  
Export: [ExportedEstimate - Azure.xlsx](./ExportedEstimate%20-%20Azure.xlsx).  
Monthly: **AUD 281.27**.

### 4.2.1.5 Cost comparison (per VM)

| Provider | Monthly (AUD) | Region | OS | vCPU/RAM | Storage |
|---|---:|---|---|---|---|
| AWS EC2 | 303.25 | Sydney | Linux | 4/16 | 384 GB |
| Azure VM | 281.27 | Australia East | Linux | 4/16 | 384 GB |

The comparison is like‑for‑like because compute, storage, OS and utilisation assumptions are aligned.

### 4.2.1.6 Five‑year total cost (all VMs)
**Formula:** Total VMs = 3 + branches; 5‑year cost = monthly × 60 × total VMs.  
For 4 branches (7 VMs): **AWS = AUD 127,363.24**; **Azure = AUD 118,133.40**. Totals will change if backups/egress or commitment discounts are included.

### 4.2.1.7 Recommendation
Azure is suggested in the replacement of the booking-server within the resonant baseline since it results in a lower total cost over 5 years but preserves an operational area in Australia.

### 4.2.1.8 Cloud VMs vs buying new servers (pros/cons)
- **Cloud:** Faster provisioning and scaling, but greater reliance on WAN/VPN and add‑on costs.  
- **On‑prem:** Local control and predictable LAN performance, but higher CAPEX and more complex DR.
