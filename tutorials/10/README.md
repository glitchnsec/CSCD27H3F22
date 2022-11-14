---
layout: default
permalink: /tutorials/10/
---

# Web Security

We learned the danger of trusting or making assumptions about user's input to web applications.

## Identifying vulnerable code

- ### Server Side Request Forgery to XML External Entity Injection

    The following excerpt has been obtained from a vulnerable version of Microsoft Exchange OnPrem and is related to [CVE-2020-17143](https://msrc.microsoft.com/update-guide/vulnerability/CVE-2020-17143) with credits to [Steven Seely of Qihoo360](https://srcincite.io/pocs/cve-2020-17143.py.txt)

    ```C#
    internal static WacUrlInfo GetWacUrl(ICallContext callContext, OwaIdentity identity, string endPointUrl, string documentUrl, bool isEdit, bool isSPGetWacTokenEnabled) {

        string actionOrAppId = isEdit ? "2" : "4";
        if (isSPGetWacTokenEnabled)
        {
            actionOrAppId = (isEdit ? "1" : "0");
        }
        string getWacTokenUrlFormat = isSPGetWacTokenEnabled ? "{0}/_api/SP.Utilities.WOPIHostUtility.GetWopiTargetPropertiesByUrl(fileUrl=@p, requestedAction={2})?@p='{1}'" : "{0}/_api/Microsoft.SharePoint.Yammer.WACAPI.GetWacToken(fileUrl=@p, wopiAction={2})?@p='{1}'";

        WebResponse tokenRequestWebResponse = OneDriveProUtilities.GetTokenRequestWebResponse(callContext, identity, getWacTokenUrlFormat, endPointUrl, documentUrl, actionOrAppId, "GetWacToken", "SP.GWT");       // 6
        XmlDocument xmlDocument = new XmlDocument();
        OneDriveProUtilities.EndBudget(callContext);
        xmlDocument.Load(tokenRequestWebResponse.GetResponseStream());              // 7
        
        //..
    }

    // [.. Code excluded for clarity ..]
    // Invocation context
    WacUrlInfo wacUrl = OneDriveProUtilities.GetWacUrl(
        callContext,
        identity,
        endPointUrl,     // Mallory controls this
        documentUrl,
        isEdit,
        isSPGetWacTokenEnabled);            // 5
    ```

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