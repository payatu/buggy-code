---
weight: 700
title: "Authentication Failures"
description: ""
lead: "Chall 1"
icon: "login"
draft: false
toc: false
images: []
menu:
  docs:
    parent: "authentication-failures"
authors: Hardeep Singh
---

{{< tabs tabTotal="2">}}
{{% tab tabName="Challenge" %}}

- This lab demonstrates how to create and manage a user session, which is a temporary and interactive exchange of information between a user and a system. It covers setting session attributes and issuing a session cookie to maintain the session.

````js {linenos=true,anchorlinenos=true}
import javax.servlet.http.Cookie;
import javax.servlet.http.HttpServletRequest;
import javax.servlet.http.HttpServletResponse;
import javax.servlet.http.HttpSession;

public class CreateSession extends HttpServlet {

    protected void doPost(HttpServletRequest request, HttpServletResponse response) throws ServletException, IOException {
        String username = request.getParameter("user");
        String password = request.getParameter("pass");

        
        if (isValidUser(username, password)) {
            HttpSession session = request.getSession(true);
            session.setAttribute("username", username);

            Cookie cookie = new Cookie("JSESSIONID", session.getId());
            response.addCookie(cookie);
            response.sendRedirect("/dashboard");
        } else {
            response.sendRedirect("/login");
        }
    }

    private boolean isValidUser(String username, String password) {
        // Validation logic
        
    }
}

````
{{% /tab %}}
{{% tab tabName="Solution" %}}


````js {linenos=table,hl_lines=[3,"5-7"],anchorlinenos=true}
Stay tuned for updates on the solution !!
````
{{% /tab %}}
{{< /tabs >}}

## References

- [https://cheatsheetseries.owasp.org/](https://cheatsheetseries.owasp.org/)
- [https://owasp.org/Top10/2025/A07_2025-Authentication_Failures/](https://owasp.org/Top10/2025/A07_2025-Authentication_Failures/)
- [https://docs.microsoft.com/en-us/dotnet/standard/security/](https://docs.microsoft.com/en-us/dotnet/standard/security/)
- [https://github.com/guardrailsio/awesome-dotnet-security](https://github.com/guardrailsio/awesome-dotnet-security)
- [https://owasp.org/Top10/2025/](https://owasp.org/Top10/2025/)