---
layout: default
permalink: /tutorials/12/
---

# Threat Hunting

Put on your investigative hats, this week we will be exploring finding mallory! 🕵️‍♀️

---

There are three main types of hunts:

- Intelligence driven
- Data driven
- Hypothesis driven

In this tutorial we will focus on **Hypothesis** driven hunt! 

## Hypothesis Driven Hunt
---

We begin by considering what Mallory might do within a victim network (building a hypothesis) and then we would test the hypothesis (given we have the data sources) by searching for evidence of the hypothetical behavior within the network. Eventually we would build alerts that will trigger when a future occurence of a behavior occurs in the future!

### What might Mallory do?
---

The [Mitre Att&ck Framework](https://attack.mitre.org/) is a catalogue of adversarial Techniques, Tactic and Procedures (a.k.a TTPs). This framework aids defenders in describing adversarial activity concisely, model detections and test secrutiy controls to name a few.

- A **Tactic** is like an objective. E.g As Mallory, I would like to:
    - Perform reconnaissance (Gather intelligence on victim)
    - Develop adversarial resources (offensive infrastructure/software engineering)
    - **Gain persistence on a compromised host or network**
    - Exfiltrate / steal data
    ...

- A **Technique** a way to achieve an objective. E.g As Mallory, I would *Gain persistence on an endpoint or network* (a Tactic) by:
    - Manipulating existing accounts
    - Creating or modifying high privilege / system services (Mallory's software/malware runs with admin privileges)
    - **Creating logon auto start scripts (these scripts run immediately a machine is booted)**
    ...

- A **Procedure** is a technical detail on how Mallory might implement a technique. E.g As Mallory, I would *Create logon auto start scripts* (a Technique) by:
    - Placing a malicious script at `C:\ProgramData\Microsoft\Windows\Start Menu\Programs\StartUp` (This is the auto startup folder for all users on a Windows)
    - Adding a malicious script, binary or commands to `rc.local` or similar scripts in a Unix-like distribution

**Discussion Q1**

- Explore the [Command and Control](https://attack.mitre.org/tactics/TA0011) Tactic.  Pick at least two distinct techniques, read it's description and discuss how Mallory leverages the technique.


Defensive security professionals (Defenders) create adversary profiles based on observed threat activity. Example: [Advanced Persistent Threat - 29 (APT 29)](https://attack.mitre.org/groups/G0016/) a.k.a [Cozy Bear](https://adversary.crowdstrike.com/en-US/adversary/cozy-bear/).

In a hypothetical hunt, the hunter assumes compromise and hunts for evidence of one or more TTPs on the endpoint or network.

### Our Hypothesis
---

Bank of Fail is major player in the financial industry, customer data security is a core business pillar. Recently threat actor D27-F22 (Mallory's fancy APT name), has been observed to compromise other banks in the region within the last six months.

This threat actor is known to leverage

- Spear Phishing for initial access
- Logon auto start scripts for persistence
- Protocol tunnelling for command and control
- Exfiltration over command and control channel

Hypothetically, Bank of Fail may have also be compromised. As a threat hunter, the organization is looking to your team to confirm or debunk this hypothesis

### The hunt
---

Hunting details may vary slightly based on the type of hunt. However, it basically involves

- Data source inventory (No logs No Crime!)
- Searching for IoCs or adversarial behavior
  - Initiate incidence response if behavior found
  - Otherwise repeat hunt on new hypothesis

You should refer to [Mitre Att&ck Framework](https://attack.mitre.org/) to inform your reasoning in the following discussion topics

**Discussion Q2**

- What data sources might you need visibility into to observe

    - Phishing attempts at Bank of Fail
    - Logon auto start scripts on Windows endpoints at Bank of Fail
    - Protocol tunnelling

**Discussion Q3**

- How might you identify (search) for rouge auto start scripts 

**Discussion Q4**

- How might you identify (search) for protocol tunnelling within Bank of Fail's network

**Discussion Q5**

- How might you develop detections to identify:

    - Phishing attempts at Bank of Fail
    - Installation of rouge auto start scripts on Windows endpoints at Bank of Fail
    - Protocol tunnelling withing Bank of Fail's network