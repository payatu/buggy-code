---
weight: 300
title: "Software Supply Chain Failures"
description: ""
icon: "stack"
date: "2025-10-15T16:21:50+05:30"
lastmod: "2025-10-15T16:21:50+05:30"
draft: false
toc: false
authors: Hardeep Singh
menu:
  docs:
    parent: "software-supply-chain-failures"
---

{{< tabs tabTotal="2">}}
{{% tab tabName="Challenge" %}}

- A widely-used, open-source logging framework for Java applications, developed by an OSS Foundation was found to be vulnerable to a critical exploit. We require your excellent skills to figure out the vulnerable framework.


````java {linenos=true,anchorlinenos=true}
package com.firstapp.register;

import java.io.IOException;
import javax.servlet.ServletException;
import javax.servlet.annotation.WebServlet;
import javax.servlet.http.HttpServlet;
import javax.servlet.http.HttpServletRequest;
import javax.servlet.http.HttpServletResponse;

import org.apache.logging.log4j.LogManager;
import org.apache.logging.log4j.Logger;



@WebServlet("/log")
public class doLog extends HttpServlet {
    private static final long serialVersionUID = 1L;
    // using log4j library 2.14.0 for logging
    private static final Logger logger = LogManager.getLogger(log4shell.class);
    
    
    protected void doGet(HttpServletRequest request, HttpServletResponse response)
            throws ServletException, IOException {
        String userAgent = request.getHeader("User-Agent");
        logger.error("User-Agent: " + userAgent);
        
    }
}


````
{{% /tab %}}
{{% tab tabName="Solution" %}}


````java {linenos=table,hl_lines=[3,"5-7"],anchorlinenos=true}
Stay tuned for updates on the solution !!
````
{{% /tab %}}
{{< /tabs >}}

## References

- [https://cheatsheetseries.owasp.org/](https://cheatsheetseries.owasp.org/)
- [https://owasp.org/Top10/2025/A03_2025-Software_Supply_Chain_Failures/](https://owasp.org/Top10/2025/A03_2025-Software_Supply_Chain_Failures/)
- [https://docs.microsoft.com/en-us/dotnet/standard/security/](https://docs.microsoft.com/en-us/dotnet/standard/security/)
- [https://github.com/guardrailsio/awesome-dotnet-security](https://github.com/guardrailsio/awesome-dotnet-security)
- [https://owasp.org/Top10/2025/](https://owasp.org/Top10/2025/)