# BeautifulSoup

## How to get attributes of the HTML element

There is the `attrs` member variable in the `bs4.element.ResultSet` object, which is returned by `find` or `find_all`. You can use it to access HTML tag attributes.

```
import requests
import bs4
from bs4 import BeautifulSoup

r=requests.get(
    'https://hk.jobsdb.com/hk/jobs/sales-cs-business-devpt/4',
    headers={
        'User-Agent': 'Mozilla/5.0 (Macintosh; Intel Mac OS X 10_10_5) AppleWebKit/537.36 (KHTML, like Gecko) Chrome/65.0.3325.181 Safari/537.36'
    }
)
mypage = BeautifulSoup(r.text)
price1 = mypage.find_all('a',attrs={'class':'posLink'})
print(price1[0].attrs['href'])
```

One output is: 

```
https://hk.jobsdb.com/hk/en/job/senior-sales-engineer-sales-engineer-100003006011403
```

