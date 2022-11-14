---
layout: default
permalink: /tutorials/10/
---

# Web Security

We learned the danger of trusting or making assumptions about user's input to web applications.

## Identifying vulnerable code

- ### Server Side Request Forgery to XML External Entity Injection

    The following excerpt has been obtained from a vulnerable version of Microsoft Exchange OnPrem and is related to [CVE-2020-17143](https://msrc.microsoft.com/update-guide/vulnerability/CVE-2020-17143) with credits to [Steven Seely of Qihoo360](https://srcincite.io/pocs/cve-2020-17143.py.txt)

    <img src="media/ssrf_xxe.svg" alt=""/>

    Can you spot the bug(s)? An attacker can control the `endPointUrl` parameter to `OneDriveProUtilities.GetWacUrl`

## Vulnerabilities in your code

You have probably implemented some web applications. Using your own experience building an application, discuss with your peers and brainstorm about:

- What functionalities required user input and how those functionalities could be safely implemented.

    Consider:

    - Whitelist/Blacklist
    - Sanitization

- What trust boundaries existed within the application and how user input could be safely transferred across boundaries

    Consider:
    - How can input be validated at any of the following boundaries (if they existed)
        - Client / Web server boundaries
        - Web server / OS boundaries
        - Web server / Database boundaries