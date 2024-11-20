# Attributes for the form element

-   `action` — The URL/path to send the request to, e.g. `"/submit"`
-   `method` — The HTTP method to use when submitting the form, e.g. `"get"`, `"post"`
    -   Note that `"put"` and `"delete"` are [not supported here](https://softwareengineering.stackexchange.com/a/211790).
    -   It's standard to use lowercase in the HTML here, even though they will appear as uppercase when read on the server.
-   `enctype` — The encoding type of the request body, e.g. `"text/plain"`
    -   Default is `"application/x-www-form-urlencoded"`
    -   This changes the format of the text sent to the server.
    -   Can only be changed from the default if `method="post"`

```html
<form action="/submit" method="post" enctype="text/plain">
  ...
</form>
```