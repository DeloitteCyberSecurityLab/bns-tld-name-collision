# Datasets of BNS TLD Name Collisions

The BNS TLD datasets were collected from July 27, 2023 to August 10, 2023.

## BNS TLD Data

|                                   | Handshake  | Decentraweb |
| --------------------------------- | ---------- | ----------- |
| Total Number of BNS TLDs          | 11,595,406 | 11,889      |
| Total Number of Collided BNS TLDs | 6,973      | 6,973       |
| Number of TLDs with DNS RRs       | 8,989,300  | 3           |
| Number of TLDs with Other Records | N/A        | 74          |


## Handshake

`Collided-Handshake-metadata.json(.zip)` contains a list of 6,973 collided TLD data.

### Metadata schema

| Name              | Description                                 | Type   |
| ----------------- | ------------------------------------------- | ------ |
| name              | TLD Strings                                 | string |
| opened_at         | Block height at which TLD auction opened    | number |
| state             | Auction status for TLD                      | string |
| owner             | Owner address associated with TLD           | string |
| hns_value         | Winning bid price (HNS)                     | number |
| days_until_expire | Number of days until TLD expires            | string |
| records           | Record data (see below)                     | array of objects  |

### Record data schema

In Handshake, there are seven types of DNS resource records (`NS`, `GLUE4`, `GLUE6`, `SYNTH4`, `SYNTH6`, `TXT` and `DS`). Please refer to [here](https://hsd-dev.org/guides/resource-records.html) for more detailed explanations of each resource record.

### Data Example

```json
{
  "data_num": 6973,
  "data": [
    ...,
    {
      "name": "tld",
      "opened_at": 16131,
      "state": "CLOSED",
      "owner": "hs1qpc096z90syv7wuk5kvxxt4dn08ur8e9kwjv5ru",
      "hns_value": 2299,
      "days_until_expire": 218.42,
      "records": [
        {
          "type": "GLUE4",
          "ns": "ns1.tld.",
          "address": "44.231.6.183"
        },
        {
          "type": "NS",
          "ns": "ns1.tld."
        }
      ]
    },
    ...
  ]
}
```

## Decentraweb

`Collided-Decentraweb-metadata.json(.zip)` contains a list of 6,973 collided TLD data.

### Metadata schema

| Name                 | Description                                                                | Type    |
| -------------------- | -------------------------------------------------------------------------- | ------- |
| name                 | TLD strings                                                                | string  |
| chain                | Blockchain TLD was registered (`ethereum` or `polygon`)                    | string  |
| token_id             | Token ID                                                                   | string  |
| minted_at            | Datetime TLD (NFT) was minted                                              | string  |
| string_type          | Type of string (`Letter`, `Emoji`, `Alphanumeric`, `Numerical` or `Mixed`) | string  |
| string_length        | Length of TLD strings                                                      | number  |
| owner                | Owner address associated with TLD                                          | string  |
| subdomain_count      | Number of subdomains associated with TLD                                   | number  |
| expiry_date          | Expiration datetime                                                        | string  |
| expired              | Whether TLD has expired or not                                             | boolean |
| has_resolver_address | Whether a resolver address is set or not                                   | boolean |
| records              | Record data (see below)                                                    | object  |

### Record data schema

| Name   | Description                                                                                                                   | Type   |
| ------ | ----------------------------------------------------------------------------------------------------------------------------- | ------ |
| wallet | Wallet addresses record which contains `BTC` and `ETH` records                                                                | object |
| dns    | DNS records which contains `A`, `MX`, `CNAME`, `TXT` and `AAAA` records                                                       | object |
| others | Other records which contains `sns`, `ipfs`, `email`, `phone`, `url`, `keywords`, `avatar`, `description` and `notice` records | object |

If you want to know more details about each record, please refer to the [official documents](https://docs.decentraweb.org/decentraweb/for-developers/full-integration-core-library) and/or [GitHub pages](https://github.com/decentraweb/decentrawebjs).

Note that `email` and `phone` values are masked because of the personal information.

### Data Exmaple

```json
{
  "data_num": 6973,
  "data": [
    ...,
    {
      "name": "knft",
      "chain": "ethereum",
      "token_id": "62243156562085017958267561360935381008803357433680823832621033116482340892363",
      "minted_at": "2023-01-07T06:16:11",
      "string_type": "Letter",
      "string_length": 4,
      "owner": "0x3211e4D9335cB406f00001Aa00e7A0e9a194c8F4",
      "subdomain_count": 1,
      "expiry_date": "2024-01-07T21:04:57",
      "expired": false,
      "has_resolver_address": true,
      "records": {
        "wallet": { "ETH": "0x50F1f9FAa448f1d0E0912A7f6147aEFa910DBe41", "BTC": null },
        "dns": { "A": null, "MX": null, "CNAME": null, "TXT": null, "AAAA": null },
        "others": {
          "sns": { "twitter": "example", "telegram": "example", "lens": "example" },
          "ipfs": null,
          "email": "masked@masked.example",
          "phone": null,
          "url": null,
          "keywords": null,
          "avatar": null,
          "description": null,
          "notice": null
        }
      }
    },
    ...
  ]
}
```

## Citing

```bibtex
@inproceedings{Ito2024,
  title={{Investigations of Top-Level Domain Name Collisions in Blockchain Naming Services}},
  author={Ito, Daiki and Takata, Yuta and Kumagai, Hiroshi and Kamizono, Masaki},
  booktitle={Proceedings of the ACM Web Conference 2024},
  series = {WWW '24},
  year={2024}
}
```
