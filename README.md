# SRC_Challanges

## How to Contribute

**Requirements**
1. golang version should be 1.22>=
2. [Hugo extended](https://github.com/gohugoio/hugo/releases)

**Important Points to remember**
1. DO NOT COMMIT TO THE MAIN BRANCH DIRECTLY.
2. DO NOT EDIT hugo.toml FILE

### Local Setup
1. The theme content is in labs directory.
2. Edit hugo.toml file and modify base url to localhost with port on which hugo is running. (Don't push this change to remote repo)
3. Use the following command from the labs directory to serve it locally

    ```
    hugo serve
    ```

### Adding Content
1. Use the following command to create markdown file for your challenge. Run the following command from the labs directory.
    ```
    hugo new content/docs/<category_name>/n.md
    ```
    Replace `category_name` with the category name available in the repo and `n` with any number not in use currently. Use the numbers sequentially not randomly.

2. Once the markdown file has been created, at the top modify title.
3. We follow the following syntax to contribute.
    ```
    {{< tabs tabTotal="2">}}
    ```
    The above tag defines the total number of tabs to be adding in the challenges
    ```
    {{% tab tabName="Challenge" %}}
    ```
    The above tag starts the first tab and set the tab name to `Challenge`
    ```
    {{% /tab %}}
    ```
    The above tag stops the tab content.
    ```
    {linenos=true,anchorlinenos=true}
    ```
    The above tag after triple backticks will show the line number, we can also add `hl_lines` to highlight line numbers. Check the below example to see what it might look like.
    Here is a complete example of what a final markdown file will look like.
    ```
        ---
        weight: 999
        title: "SQLi 1"
        description: ""
        icon: "article"
        date: "2023-12-14T14:34:57+05:30"
        lastmod: "2023-12-14T14:34:57+05:30"
        draft: false
        toc: true
        ---

        Challenge description

        {{< tabs tabTotal="2">}}
        {{% tab tabName="Challenge" %}}

        ````js {linenos=true,anchorlinenos=true}
        challenge snippet
        ````

        {{% /tab %}}
        {{% tab tabName="Solution" %}}

        Solution steps or description

        ````js {linenos=table,hl_lines=[3,"5-7"],anchorlinenos=true}
        solution snippet
        ````


        {{% /tab %}}
        {{< /tabs >}}
    ```

4. Run it locally and once done, commit to another branch and raise a merge request to main branch.
5. Request review from the team.

And we are done :D Thank you for reading.

