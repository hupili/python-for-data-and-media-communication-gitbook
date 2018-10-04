# requests

## Modify User Agent

Some websites combat crawler by detecting the [user agent](https://en.wikipedia.org/wiki/User_agent). User agent can be simply regarded as the name of your browser. Websites may stop your HTTP request if it detects you are not using a normal browser. That is because `requests` will tell the website its identity by default. You can modify this behaviour using `headers` parameter of `requests.get`:

```
r = requests.get(url, headers = {'user-agent': 'Put-User-Agent-String-Here'})
```

Use [Open Rice](openrice.com) as an example:

```
url = 'https://www.openrice.com/en/hongkong/restaurants?what=sushi'
r = requests.get(url, headers = {'user-agent': 'Mozilla/5.0 (Macintosh; Intel Mac OS X 10_13_3) AppleWebKit/537.36 (KHTML, like Gecko) Chrome/64.0.3282.167 Safari/537.36'})
```

A more complete experiment can be found [here](https://github.com/hupili/python-for-data-and-media-communication/blob/master/w4-scraper/Open%20Rice.ipynb)

## HTTP status code

When you make a request to a website, there might be different status responded. Common examples here:

- 200 OK
- 400 Bad Request
- 401 Unauthorized
- 403 Forbidden

For more examples, please refer to [here](https://en.wikipedia.org/wiki/List_of_HTTP_status_codes) .