---
weight: 200
title: "Security Misconfiguration"
description: ""
icon: "security"
date: "2025-10-15T16:21:50+05:30"
lastmod: "2025-10-15T16:21:50+05:30"
draft: false
toc: false
authors: Mitul Kumar
menu:
  docs:
    parent: "security-misconfiguration"
---

{{< tabs tabTotal="2">}}
{{% tab tabName="Challenge" %}}

- Our new intern has worked hard on this project allowing authenticated users to download files, but we are afraid if everything is in order? We seek your expertise to ensure that the application is secure and adheres to best practices.

````js {linenos=true,anchorlinenos=true}
const session = require("express-session");

const app = express();

app.use(session({
    secret: process.env.SESSION_SECRET,
    resave: false,
    saveUninitialized: true
}));

app.use(express.urlencoded({ extended: false }));

function loginRequired(req, res, next) {
    if (!req.session.userId) {
        return res.status(403).send('Forbidden');
    }
    const user = checkUser(req.session.userId) // checkUser checks if a valid user exist or not.
    if(user!=null) {
        next()
    } 
    else {return res.status(403).send('Forbidden');

    }
}

app.get("/dashboard", loginRequired, (req, res) => {
    res.send("Hello, Welcome to the dashboard!");
    res.end();
});

app.post("/download", loginRequired, (req, res) => {
    const file = req.body.file;
    res.download(file);
});

app.listen(3000, () => {
    console.log("Application started");
});
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
- [https://owasp.org/Top10/2025/A02_2025-Security_Misconfiguration/](https://owasp.org/Top10/2025/A02_2025-Security_Misconfiguration/)
- [https://docs.microsoft.com/en-us/dotnet/standard/security/](https://docs.microsoft.com/en-us/dotnet/standard/security/)
- [https://github.com/guardrailsio/awesome-dotnet-security](https://github.com/guardrailsio/awesome-dotnet-security)
- [https://owasp.org/Top10/2025/](https://owasp.org/Top10/2025/)