# Smart Contract Audit Database Public API Documentation

Being a pioneer in providing independent smart contract security audits and one of the leading DeFi projects promoting the highest security standards for the industry, DeFiYield made the next step towards making the DeFi space safer for everyone - released the unique audit database and the Safe API.  

The Safe API gives access to the only database containing all available security audits for DeFi projects performed by DeFiYield and other top industry auditing providers: Quantstamp, PeckShield Inc., Chainsulting, Open Zeppelin, ConsenSys Diligence, Trail of Bits, CertiK, Haechi,. Solidified, Hacken, Slowmist, Omniscia, iosiro, Obelisk, CoinFabrik, DeFi Safety,  Solidity Finance, Víðarr the Auditor and SlowMist. The list of auditors can be expanded with the growth of the blockchain security branch. The DeFiYield safe audit database is dynamic and being constantly updated.

The database helps users to do the obligatory step of their due diligence before investing in DeFi projects - estimating security level of the selected projects in the most convenient and time efficient way, as users don’t need to search for audit reports all over the internet. Everything is already gathered by DeFiYield in one place. 

The API allows users to get information on about 300 projects running on different chains: Ethereum, Binance Smart Chain, HECO, Polygon, Fantom, Avax, Harmony, xDAI, OKExChain, Polkadot. And the database is being systematically replenished with projects built on newly developed, innovative and more scalable blockchain solutions.  

**The information available with the API includes:**

+ Project name
+ Token ticker and address
+ Chain name
+ Auditor name
+ Number of security issues revealed during the auditing
+ Security scoring (if provided by the auditor)
+ Audit date 
+ Link to the pdf file containing the audit report, which can be easily downloaded.

Each audit provider has its own approach to the project safety analysis. Some auditors only perform automated checks, others do manual reviews or combine automated and manual techniques.

Moreover, the auditors listed review different sets of metrics to assess security of DeFi projects. Some are only focused on checking smart contracts vulnerabilities, others consider non-code project characteristics along with the technical part. Even the latter can be done with different approaches, covering different types of code vulnerabilities.  

Thus, the ability to see different security estimation results and compare them enables getting the fullest picture about a project’s advantages and disadvantages from the security perspective.

To provide comparability of security auditing results featured by different auditors for each project, DeFiYield decided to show summaries in form of the numbers of issues found by each auditor, excluding already fixed issues with the consent of both parties - the auditors and the projects, which can be seen in the reports. But this metric doesn’t fully reflect if a DeFi project is safe to invest in. To get the complete understanding of all possible risks related to interaction with the project, it’s necessary to fully review the audit reports, taking their methodology into consideration.  

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


## Audit list

Calling the audit endpoint returns the list of audits.

**Audit list request example:**

URL: https://api.safe.defiyield.app/audit/list

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
"project_name": "Pickle Finance",
"project_link": "https://pickle.finance/",
"token_ticker": "PICKLE",
"token_address":"0x429881672B9AE42b8EbA0E26cD9C73711b891Ca5"
   },
   {
     "project_name": "ARMOR",
     "project_link": "https://armor.fi/",
     "token_ticker": "ARMOR",
     "token_address": "0x1337def16f9b486faed0293eb623dc8395dfe46a"
    }
  }
]
```


## Audits by token addresses

This endpoint requires a token address(es) and returns a list of audits available for the requested address(es).


**Request example for audits by token addresses:**

URL: https://api.safe.defiyield.app/audit/address

Method: POST

Headers:
```yaml
Authorization: Bearer ${yourToken}
```

Body:
```yaml
{
  “addresses”: [
      “0xBf494F02EE3FdE1F20BEE6242bCe2d1ED0c15e47”,
      ”0x40304195abab064a0f4444acb6e7556d9f492b98”
  ]
}
```

**Response example:** 

```yaml
 [
   {
    "id": 303,
    "project_name": "ARMOR",
    "project_link": "https://armor.fi/",
    "logo_link": "safe/files/audit/logo/60a7fd7a67f6f.png",
    "token_ticker": "ARMOR",
    "token_address": "0x1337def16f9b486faed0293eb623dc8395dfe46a",
    "network": {
      "id": 1,
      "name": "Ethereum"
    },
    "auditFile": [
      {
        "id": 298,
        "name": null,
        "score": null,
        "tech_issues": null,
        "tech_issues_low": null,
        "tech_issues_medium": null,
        "tech_issues_high": null,
        "date": null,
        "audit_link": null
      }
    ],
    "partnerAudits": [
      {
        "id": 355,
        "name": "Smart contracts",
        "tech_issues": 5,
        "tech_issues_low": null,
        "tech_issues_medium": null,
        "tech_issues_high": null,
        "date": "2021-01-14",
        "audit_link": "safe/files/audit/pdf/HAECHI_AUDIT_Armor_Smart_Contract_Audit_Report_v2_0_1.pdf",
        "partner": {
          "id": 19,
          "name": "Haechi"
        }
      }
    ]
  }
]
```


## Other API components

Along with the audit database, the API will soon enable reaching the database of DeFi scams and the Smart Contract Weaknesspedia, containing information about all currently known smart contract code vulnerabilities, including DeFi-specific ones.  




