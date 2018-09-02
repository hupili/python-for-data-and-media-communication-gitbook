# Week 06 - Advanced scraping: browser emulation, anti-crawler and other nitty gritty

<div id="toc">

<!-- TOC -->

- [Week 06 - Advanced scraping: browser emulation, anti-crawler and other nitty gritty](#week-06---advanced-scraping-browser-emulation-anti-crawler-and-other-nitty-gritty)
    - [Anti-crawling](#anti-crawling)
        - [User agent](#user-agent)
        - [Rate throttling](#rate-throttling)
    - [Common issues](#common-issues)
        - [Encoding](#encoding)
    - [Browser emulation](#browser-emulation)
        - [Selenium](#selenium)
        - [splinter](#splinter)
    - [Analyse Network Traces](#analyse-network-traces)
    - [Crawl mobile Apps](#crawl-mobile-apps)

<!-- /TOC -->

</div>

## Anti-crawling

### User agent

### Rate throttling

* Limit by IP
* Limit by cookie/ access token

## Common issues

### Encoding

[51job.com example](https://github.com/hupili/python-for-data-and-media-communication/blob/a4922340f55c4565fff19979f77862605ac19f22/scraper-examples/51job.com.ipynb)

## Browser emulation

### Selenium

https://github.com/hupili/python-for-data-and-media-communication/tree/a4922340f55c4565fff19979f77862605ac19f22/ww-selenium

[libguides example](https://github.com/hupili/python-for-data-and-media-communication/blob/a4922340f55c4565fff19979f77862605ac19f22/scraper-examples/Libguides.ipynb)

### splinter

https://github.com/hupili/python-for-data-and-media-communication/tree/master/ww-splinter

## Analyse Network Traces

Open "Google Chrome Developer Console" by `command+option+i`. Check out the "Network" tab and use "XHR" filter to find potential packages. We are usually interested in `json` files or `xml` files sent over the line. Most dynamic web pages have predictable / enumerable internal API -- use HTTP request to get certain `json`/ `xml` files.

Some websites render HTML at the backend and send them to the frontend in a dynamic way. You find the URL in address bar stays the same but the content is changed. You can also find the HTML files and their **real URL** via developer console. One such example is [xiachufang.com scraper](https://github.com/hupili/python-for-data-and-media-communication/blob/a4922340f55c4565fff19979f77862605ac19f22/scraper-examples/xiachufang.com.ipynb).

## Crawl mobile Apps

**TODO**

"Charles proxy", "mitmproxy"