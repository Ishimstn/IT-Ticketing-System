# ServiceNow ITSM Administration & Ticket Lifecycle Lab

## 📌 Project Overview
This project demonstrates the implementation, configuration, and end-to-end administration of an enterprise IT Service Management (ITSM) system using a **ServiceNow Personal Developer Instance (PDI)**. 

The goal of this lab was to transition from theoretical ITIL knowledge to practical execution by designing a functional service desk, establishing user hierarchies, configuring strict Service Level Agreements (SLAs), and simulating a multi-tier technical escalation and resolution cycle.

---

## 🛠️ Technologies & Concepts Demonstrated
* **SaaS Platform Administration:** ServiceNow (Classic / Next Experience Interface).
* **ITIL v4 Framework:** Incident Management, Service Operations, and Request Fulfillment.
* **User & Role Management:** Provisioning users, managing assignment groups, and configuring inherited `itil` fulfillment roles.
* **SLA Engineering:** Developing automated countdown timers based on custom urgency-impact matrices.
* **Technical Documentation:** Generating professional runbooks, system configuration metrics, and diagnostic logs.

---

## 📊 System Architecture & Hierarchical Structure

```text
ServiceNow Instance (dev181263)
├── 👥 User Directory (sys_user)
│   ├── 👤 John Doe (jdoe) ────────────── [Role: No Roles - End User]
│   ├── 👩‍💻 Jane Smith (jsmith) ────────── [Role: ITIL Agent]
│   └── 👨‍💻 Bob Johnson (bjohnson) ─────── [Role: ITIL Agent]
│
└── 🛠️ Assignment Groups (sys_user_group)
    ├── 📂 Service Desk - Tier 1 ──────── [Member: Jane Smith]
    └── 📂 Network Infrastructure - Tier 2 [Member: Bob Johnson]
```



## 🚀 Step-by-Step Implementation

### Phase 1: Environment Provisioning & Org Setup
1. **Tenant Initialization:** Requested and configured a dedicated ServiceNow developer tenant (Instance `dev181263`).
2. **Assignment Groups:** Created two functional divisions:
   * **Service Desk - Tier 1:** Frontline ticket triage and basic troubleshooting.
   * **Network Infrastructure - Tier 2:** High-level routing, switching, and domain replication troubleshooting.
3. **User Directory Provisioning:** Created accounts for `John Doe` (Customer), `Jane Smith` (Tier 1 Agent), and `Bob Johnson` (Tier 2 Agent).
4. **Role Allocation:** Assigned the system `itil` role to both agents to grant ticket-handling and task fulfillment permissions.

<h2 align="center">Creating Tier 1 Group</h2>
<p align="center">
  <img src="https://i.imgur.com/gOWv4bU.png" width=80%
</p>
<br />
<h2 align="center">Creating Tier 2 Group</h2>
<p align="center">
  <img src="https://i.imgur.com/UYS2LQu.png" width=80%
</p>
<h2 align="center">Creating User Records</h2>
<p align="center">
  <img src="https://i.imgur.com/E3l8yH8.png" width=80%>
  <br />
  <img src="https://i.imgur.com/EipCs4y.png" width=80%>
  <br />
  <img src="https://i.imgur.com/zk62ou9.png" width=80%>
</p>
<h2 align="center">Configuring Users to Correct Assignment Groups</h2>
<p align="center">
  <img src="https://i.imgur.com/4mtxFBk.png" width=80%>
  <br />
  <img src="https://i.imgur.com/LWnuKEh.png" width=80%>


### Phase 2: SLA Configuration
To enforce operational accountability, designed an automated **2-Hour Resolution SLA** for critical tickets.
* **Start Condition:** Incident state is `Active` AND Urgency is `1 - High`.
* **Stop Condition:** Incident state is `Resolved`.
* **Schedule:** Configured to run on a **24x7** continuous operational schedule.

<h2 align="center">Creating SLA with Start Condition</h2>
<p align="center">
    <img src="https://i.imgur.com/jcQUTAc.png" width=80%>
</p>
<br />
<h2 align="center">SLA with Stop Condition</h2>
<p align="center">
    <img src="https://i.imgur.com/0jM0lKJ.png" width=80%>
</p>


### Phase 3: The Incident Lifecycle & Technical Escalation

#### 1. Ticket Submission (The Customer Entry)
* **Caller:** John Doe
* **Category:** Password Reset
* **Urgency:** 1 - High *(Triggered the automated 2-Hour SLA clock)*
* **Symptom:** User locked out of local domain workstation following consecutive bad password attempts.
<h2 align="center">Incident Report by End User</h2>
<p align="center">
    <img src="https://i.imgur.com/ubGQEi2.png" width=80%>
</p>

#### 2. Frontline Triage (Tier 1 Support)
* **Assigned Group:** Service Desk - Tier 1
* **Assigned Agent:** Jane Smith
* **Diagnostic Actions:** Analyzed directory logs, attempted a credential cache reset, and documented actions in the **Internal Work Notes**.
<h2 align="center">Assigning Service Desk Tier 1 to Incident</h2>
<p align="center">
    <img src="https://i.imgur.com/LzfFKho.png" width=80%>
</p>

#### 3. Engineering Escalation (Tier 2 Support)
* **Escalation Path:** Transferred to Network Infrastructure - Tier 2 due to a domain controller synchronization delay.
* **Assigned Agent:** Bob Johnson
* **Resolution:** Bob forced database replication across secondary domain controllers, re-authenticated the local cache, and successfully resolved the incident.
* **SLA Status:** Incident resolved in compliance, freezing the SLA countdown clock.
<h2 align="center">Escalating Incident to Tier 2 Support</h2>
<p align="center">
    <img src="https://i.imgur.com/11M4GUs.png" width=80%>
</p>
<h2 align="center">Resolving Incident with Tier 2 Support</h2>
<p align="center">
    <img src="https://i.imgur.com/RIqEsQj.png" width=80%>
</p>

## 🔑 Key Takeaways & Skills Gained
* **Enterprise Queue Management:** Learned how to navigate complex cloud-hosted ITSM platforms to ensure work is triaged and routed efficiently.
* **Interdepartmental Escalation:** Gained a hands-on understanding of how different support tiers interact, pass technical context via work notes, and cooperate to solve complex infrastructure blocks.
* **SLA Compliance:** Learned the importance of meeting business agreements and tracking performance metrics in real-time.
