# Rekt Database Public API Documentation

Striving to remain the biggest contributor into the safety of the DeFi community, DeFiYield has developed a unique Rekt Database of rug pulls, abandoned projects and flash loan attacks. It can help users to know whom they should stay away from and learn the most frequent rug pull and flash-loan patterns in order to be able to distinguish safe projects with real value from the risky and scammy ones.

The API allows accessing detailed information about over 500 scam, exploit and flash-loan attack cases. The database is being regularly updated with new information.

**The information available with the API includes:**

+ Project name
+ Token ticker and address
+ Logo icon
+ Scam/Attack Date
+ Description
+ Proof link
+ Website link
+ Webarchive link
+ Funds Lost

The Description part provides users with facts about the scam and flash-loan cases, which were manually checked by the DeFiYield team through analyzing blockchain transactions. The revealed information includes smart contract weaknesses used in the attacks and scams, smart contract functions called and their consequences, roles having triggered the functions (e.g. contract deployer, contract owner), etc.

## How to use the API 

In order to use the API, you first need to register as a user and receive an individual token. This token will allow making requests for authorization by the Bearer authentication type in the future.


### User registration

**Registration request example:**

URL: https://api.safe.defiyield.app/user/register

Method: POST

Body:
```yaml
{
  “username”: “string”
  “email”: “string”
}
```
**Response example:** 

```yaml
{
  "message": "Registration successful.",
  "status": true,
  "token": "f3299a75-7rd3-20a8-ab02-b34f7172dac7"
}
```

After the registration is completed, you will receive the token enabling further requests for other API endpoints.


## Scam list

Calling the scam database endpoint returns the list of scams.

**Scam list request example:**

URL: https://api.safe.defiyield.app/scams/list

Method: POST

Headers:
```yaml
Authorization: Bearer ${yourToken}
```
Body:
```yaml
{}
```

**Response example:** 

```yaml
[
  {
        "id": 37,
        "project_name": "AMPLYFI",
        "description": null,
        "token_name": "AYFI",
        "token_address": "0x8a3c3334502ce5c7cf81c4cc05d5ab06a4d505b2",
        "logo_link": "safe/files/scamDatabase/logo/60d4d6b54a7d3.png",
        "date": "2020-10-06",
        "proof_link": null,
        "website_link": "http://amplyfi.money/",
        "webarchive_link": "https://web.archive.org/web/20201007000549/https://amplyfi.money/",
        "funds_lost": "850"
    },
    {
        "id": 38,
        "project_name": "Foxy.farm",
        "description": null,
        "token_name": "FOXY",
        "token_address": "0x735c98ae8cd26b732a23c3889f237c5633b9f997",
        "logo_link": "safe/files/scamDatabase/logo/60d4d7f2c83a2.png",
        "date": "2020-10-20",
        "proof_link": null,
        "website_link": null,
        "webarchive_link": null,
        "funds_lost": "8"
    }
]
```


## Scams by token addresses

This endpoint requires a token address(es) and returns a list of scams available for the requested address(es).


**Request example for scam cases by token addresses:**

URL: https://api.safe.defiyield.app/scams/address

Method: POST

Headers:
```yaml
Authorization: Bearer ${yourToken}
```

Body:
```yaml
{
    "addresses": ["0x8a3c3334502ce5c7cf81c4cc05d5ab06a4d505b2", "0x0209ce3516587cc4a22b54c024b2ee724c117036"]
}
```

**Response example:** 

```yaml
 [
    {
        "id": 50,
        "project_name": "MiniVault.Finance",
        "description": null,
        "token_name": "miniCORE",
        "token_address": "0x0209ce3516587cc4a22b54c024b2ee724c117036",
        "logo_link": "safe/files/scamDatabase/logo/60d4e1c4d251f.png",
        "date": "2020-11-26",
        "proof_link": "https://twitter.com/WARONRUGS/status/1331849165974990849",
        "website_link": "https://minivault.finance/",
        "webarchive_link": "https://web.archive.org/web/20201104144320/https://minivault.finance/",
        "funds_lost": "20"
    },
    {
        "id": 37,
        "project_name": "AMPLYFI",
        "description": null,
        "token_name": "AYFI",
        "token_address": "0x8a3c3334502ce5c7cf81c4cc05d5ab06a4d505b2",
        "logo_link": "safe/files/scamDatabase/logo/60d4d6b54a7d3.png",
        "date": "2020-10-06",
        "proof_link": null,
        "website_link": "http://amplyfi.money/",
        "webarchive_link": "https://web.archive.org/web/20201007000549/https://amplyfi.money/",
        "funds_lost": "850"
    }
]
```


## Other API components

Along with the scam database, the API enables reaching the recently launched audit database. Moreover, DeFiYield is going to release the Smart Contract Weaknesspedia soon, which contains information about all currently known smart contract code vulnerabilities, including DeFi-specific ones. 




