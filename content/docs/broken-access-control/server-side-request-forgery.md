---
weight: 101
title: "Server-Side Request Forgery (SSRF)"
description: ""
icon: "storage"
date: "2025-10-15T16:21:50+05:30"
lastmod: "2025-10-15T16:21:50+05:30"
draft: false
toc: false
authors: Mukund Kedia
menu:
  docs:
    parent: "server-side-request-forgery"
---

{{< tabs tabTotal="2">}}
{{% tab tabName="Challenge" %}}

- Occasionally, certain requests are not visible on the Burp proxy as they are internal. However, these internal requests can still be exploited, We require your excellent skills to figure out the vulnerability.

HomeController.cs
````csharp {linenos=true,anchorlinenos=true}
using Microsoft.AspNetCore.Mvc;
using MvcApp.Models;
using System.Diagnostics;
using System.Data.SqlClient;
using System.Net;

namespace MvcApp.Controllers
{
    public class DataController : Controller
    {

        public IActionResult Index()
        {
            return View();
        }

        [HttpPost]
        public IActionResult FetchData ([FromBody] WeatherData wdata)
        {
            Debug.WriteLine("FetchData function!");
            string latitude = wdata.latitude;
            string longitude = wdata.longitude;
            string weatherurl = wdata.weatherurl;

            string modweatherurl = wdata.weatherurl + "?latitude=" + latitude + "&longitude=" + longitude + "&current=temperature_2m";

            HttpWebRequest request = (HttpWebRequest)HttpWebRequest.Create(modweatherurl);
            request.Method = "GET";
            String test = String.Empty;
            using (HttpWebResponse response = (HttpWebResponse)request.GetResponse())
            {
                Stream dataStream = response.GetResponseStream();
                StreamReader reader = new StreamReader(dataStream);
                test = reader.ReadToEnd();
                reader.Close();
                dataStream.Close();
            }
            return Content(test);
            
        }

        [ResponseCache(Duration = 0, Location = ResponseCacheLocation.None, NoStore = true)]
        public IActionResult Error()
        {
            return View(new ErrorViewModel { RequestId = Activity.Current?.Id ?? HttpContext.TraceIdentifier });
        }
    }

    public class WeatherData
    {
        public string latitude { get; set; }
        public string longitude { get; set; }
        public string weatherurl { get; set; }
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
- [https://owasp.org/Top10/2025/A01_2025-Broken_Access_Control/](https://owasp.org/Top10/2025/A01_2025-Broken_Access_Control/) 
- [https://docs.microsoft.com/en-us/dotnet/standard/security/](https://docs.microsoft.com/en-us/dotnet/standard/security/)
- [https://github.com/guardrailsio/awesome-dotnet-security](https://github.com/guardrailsio/awesome-dotnet-security)
- [https://owasp.org/Top10/2025/](https://owasp.org/Top10/2025/)