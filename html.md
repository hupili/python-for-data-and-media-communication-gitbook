# HTML FAQ

## href attribute in a tag

The `href` attribute is a URL pointing another resource from current page. There are several schemas for the `href` attribute in `<a>` tag:

```text
http://yourdomain.com/images/example.png
//yourdomain.com/images/example.png
/images/example.png
images/example.png
```

Suppose the URL of your current page is (notice the "s" in protocol part)

```text
https://mydomain.com/documents/index.html
```

The above "partial forms will be automatically converted by your web browser to following results:

```text
http://yourdomain.com/images/example.png
https://yourdomain.com/images/example.png
https://mydomain.com/images/example.png
https://mydomain.com/documents/images/example.png
```

Explanation:

1. href starting with `http://`, `https://`, or `//` are fully qualified URLs. Browser will use the string as full URL directly.
2. href starting with `//` is protocol agnostic, i.e. the resources can be accessed by either `http` or `https`. So the browser refers to the protocol used by current page to complete the protocol part.
3. The browser uses protocol and domain to complete the URL because the href starts with `/`, meaning reference to the "root folder" on this web server.
4. This needs to be contrasted with 3rd form. The href is just a relative path, i.e. without prefixing `/`. The browser uses protocol, domain and path of current page (`https://mydomain.com/documents/`) to complete the URL.

Read more on [Stack Overflow](https://stackoverflow.com/questions/2005079/absolute-vs-relative-urls) and [Wikipedia](https://en.wikipedia.org/wiki/Uniform_Resource_Identifier#Generic_syntax)