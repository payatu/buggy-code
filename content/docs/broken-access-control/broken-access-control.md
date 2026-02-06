---
weight: 100
title: "Broken Access Control"
description: ""
icon: "passkey"
draft: false
images: []
menu:
  docs:
    parent: "broken-access-control"
toc: false
authors: Hardeep Singh
---

{{< tabs tabTotal="2">}}
{{% tab tabName="Challenge" %}}

- In this challenge, you are presented with a code that involves the logic for retrieving and displaying the user's profile. Your task is to identify any vulnerabilities present in the code.

````js {linenos=true,anchorlinenos=true}
import java.io.IOException;
import javax.servlet.ServletException;
import javax.servlet.http.HttpServlet;
import javax.servlet.http.HttpServletRequest;
import javax.servlet.http.HttpServletResponse;
import java.sql.Connection;
import java.sql.DriverManager;
import java.sql.PreparedStatement;
import java.sql.ResultSet;
import java.sql.SQLException;

public class CheckProfile extends HttpServlet {
    protected void doGet(HttpServletRequest request, HttpServletResponse response) throws ServletException, IOException {
        String requestedUserId = request.getParameter("id");
        String userProfile = fetchUserProfile(requestedUserId);

        if (userProfile != null) {
            response.getWriter().println("User Profile:");
            response.getWriter().println(userProfile);
        } else {
            response.getWriter().println("User profile not found or unauthorized access");
        }
    }

    private String fetchUserProfile(String userId) {
        // Database query 
        String userProfile = null;
        try {
            Class.forName("com.mysql.cj.jdbc.Driver");
            Connection con = DriverManager.getConnection(DatabaseConfig.getJdbcUrl(), DatabaseConfig.getUsername(), DatabaseConfig.getPassword());
            PreparedStatement pst = con.prepareStatement("select * from users where id = ?");
            pst.setString(1, userId);
            ResultSet rs = pst.executeQuery();

            if (rs.next()) {
                userProfile = "User ID: " + rs.getString("id") + ", Name: " + rs.getString("name") + ", Email: " + rs.getString("email");
            }

            rs.close();
            pst.close();
            con.close();
        } catch (SQLException | ClassNotFoundException e) {
            e.printStackTrace(); 
        }
        return userProfile;
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
- [https://owasp.org/Top10/2025/A01_2025-Broken_Access_Control/](https://owasp.org/Top10/2025/A01_2025-Broken_Access_Control/) 
- [https://docs.microsoft.com/en-us/dotnet/standard/security/](https://docs.microsoft.com/en-us/dotnet/standard/security/)
- [https://github.com/guardrailsio/awesome-dotnet-security](https://github.com/guardrailsio/awesome-dotnet-security)
- [https://owasp.org/Top10/2025/](https://owasp.org/Top10/2025/)