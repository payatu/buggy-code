---
weight: 1000
title: "Mishandling of Exceptional Conditions"
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

- The code is meant to handle file operation. Beneath the straightforward logic lies an unconventional execution flow that subtly alters the program’s behavior.


````java {linenos=true,anchorlinenos=true}
import java.io.BufferedReader;
import java.io.FileReader;
import java.io.IOException;

public class FileHandlerDemo {

    public static void main(String[] args) {
        readFile("sample.txt");
    }

    public static void readFile(String filePath) {
        System.out.println("Starting file read operation...");

        try (BufferedReader br = new BufferedReader(new FileReader(filePath))) {
            String line;
            int lineCount = 0;

            while ((line = br.readLine()) != null) {
                lineCount++;
                System.out.println(line);
            }

            System.out.println("Total lines read: " + lineCount);

            throw new RuntimeException("Forced exception after file processing");

        } catch (IOException e) {
            throw new RuntimeException("File handling failed: " + e.printStakeTrace(), e);
        }
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
- [https://owasp.org/Top10/2025/A10_2025-Mishandling_of_Exceptional_Conditions/](https://owasp.org/Top10/2025/A10_2025-Mishandling_of_Exceptional_Conditions/)
- [https://docs.microsoft.com/en-us/dotnet/standard/security/](https://docs.microsoft.com/en-us/dotnet/standard/security/)
- [https://github.com/guardrailsio/awesome-dotnet-security](https://github.com/guardrailsio/awesome-dotnet-security)
- [https://owasp.org/Top10/2025/](https://owasp.org/Top10/2025/)