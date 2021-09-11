# PYTHON-AMAZON-AD-API [AMAZON ADVERTISING]

![CodeQL](https://img.shields.io/badge/coverage-15%25-yellow)

Python Amazon Advertising Api

### Set Up

Create a .env file and put in the root of your project ( SANDBOX or PRODUCTION )
```
# environment variables defined inside a .env file
AWS_ENV=SANDBOX
```
<pre><code>.
├── .env
└── campaign_client.py
</code></pre>

### Credentials
Use a credentials.yml file with your credentials if you dont know how to obtain your refresh token, please visit:

[Login with Amazon application](https://advertising.amazon.com/API/docs/en-us/setting-up/step-1-create-lwa-app)

```
version: '1.0'

default:
  refresh_token: 'your-refresh-token'
  client_id: 'your-client-id'
  client_secret: 'your-client-secret'
  profile_id: 'your-profile-id'

```

* macOS and Other Unix:
* Windows: 

<div>
<h3>Search Paths ¶</h3>
<ul>
<li>macOS Other Unix: <code><span>~/.config/python-ad-api</span></code></li>
<li>Windows: <code><span>%APPDATA%\python-ad-api</span></code> where the <cite>APPDATA</cite> environment variable falls
back to <code><span>%HOME%\AppData\Roaming</span></code> if undefined</li>
</ul>
</div>

[Confuse](https://confuse.readthedocs.io/en/latest/usage.html#search-paths)


### Usage Campaigns

```
import logging
from ad_api.base import AdvertisingApiException, Marketplaces
from ad_api.api.sp import Campaigns

logging.basicConfig(
    level=logging.DEBUG,
    format="%(asctime)s:%(levelname)s:%(message)s"
)

try:

    states = 'enabled'

    res = Campaigns(Marketplaces.ES).list_campaigns_extended_request(
        stateFilter=states
    )

    campaigns = res.payload
    for campaign in campaigns:
        logging.info(campaign)

    logging.info(len(campaigns))


except AdvertisingApiException as ex:
    print(ex)

```

### LICENSE

![License](https://img.shields.io/badge/license-MIT-green)
