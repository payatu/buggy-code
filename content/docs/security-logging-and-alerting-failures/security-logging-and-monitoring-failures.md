---
weight: 900
title: "Security Logging & Alerting Failures"
description: ""
icon: "monitor"
date: "2025-10-15T16:21:50+05:30"
lastmod: "2025-10-15T16:21:50+05:30"
draft: false
toc: false
authors: Mukund Kedia
menu:
  docs:
    parent: "security-logging-and-alerting-failures"
---

{{< tabs tabTotal="2">}}
{{% tab tabName="Challenge" %}}

- The code is meant to handle user authentication, but unfortunately, it contains a vulnerability. A bonus vulnerability is also present, can you spot that as well?

````csharp {linenos=true,anchorlinenos=true}
using System;
using System.Data;
using System.Data.SqlClient;
using Microsoft.AspNetCore.Mvc;

public class Clients
{
    public string email { get; set; }
    public string password { get; set; }
}

[HttpPost]
public IActionResult LoginUser([FromBody] Clients model)
{
    var email = model.email;
    var password = model.password;

    string constring = "Data Source=localhost\\sqlexpress;Initial Catalog=testdb;Integrated Security=True";

    var log = "User " + email + " logged in.";

    using (SqlConnection con = new SqlConnection(constring))
    {
        con.Open();
        string query = "INSERT INTO logs (log) values (@log)";
        SqlParameter logParam = new SqlParameter("@log", SqlDbType.NVarChar, 50);
        logParam.Value = log;

        using (SqlCommand cmd = new SqlCommand(query, con))
        {
            SqlDataReader reader = cmd.ExecuteReader();
        }
    }

    using (SqlConnection con = new SqlConnection(constring))
    {
        con.Open();
        string query = "SELECT * FROM clients WHERE email=@email AND password=@password";
        SqlParameter emailParam = new SqlParameter("@email", SqlDbType.NVarChar, 50);
        emailParam.Value = email;
        SqlParameter passwordParam = new SqlParameter("@password", SqlDbType.NVarChar, 50);
        passwordParam.Value = password;

        using (SqlCommand cmd = new SqlCommand(query, con))
        {
            SqlDataReader reader = cmd.ExecuteReader();
            if (reader.HasRows)
            {
                return Content("Login successful");
            }
            else
            {
                return Content("Login unsuccessful");
            }
        }
    }
}
````
{{% /tab %}}
{{% tab tabName="Solution" %}}

````csharp {linenos=table,hl_lines=[3,"5-7"],anchorlinenos=true}
Stay tuned for updates on the solution !!
````
{{% /tab %}}
{{< /tabs >}}

## References

- [https://cheatsheetseries.owasp.org/](https://cheatsheetseries.owasp.org/)
- [https://owasp.org/Top10/2025/A09_2025-Security_Logging_and_Alerting_Failures/](https://owasp.org/Top10/2025/A09_2025-Security_Logging_and_Alerting_Failures/)
- [https://docs.microsoft.com/en-us/dotnet/standard/security/](https://docs.microsoft.com/en-us/dotnet/standard/security/)
- [https://github.com/guardrailsio/awesome-dotnet-security](https://github.com/guardrailsio/awesome-dotnet-security)
- [https://owasp.org/Top10/2025/](https://owasp.org/Top10/2025/)