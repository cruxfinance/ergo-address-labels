# ergo-address-labels

This repo is used to keep track of all the different public addresses in use by
the different protocols to give some user friendly metadata in for example the
Cruxfinance frontend, but is free to be used by other projects, such as wallets.

## How to contribute

Each project is responsible for submitting their address metadata through PR's.
To ensure the source is correct make sure the PR is originating from the github
defined in the json.

1. Fork this repo
2. Create a new file, called [yourproject].json in the labels folder or adjust
   if one already exists for your project.
3. The json should follow the structure defined below.
4. Once done create a PR to merge back into this repository

## JSON structure

### Main structure

| field name        | description                                                 | data type      | required |
| ----------------- | ----------------------------------------------------------- | -------------- | -------- |
| organisation_name | Full name of the organistation responsible for the contract | string         | yes      |
| github            | Url to the github organisation                              | string         | yes      |
| url               | Url to the website                                          | string         | no       |
| socials           | Links to socials for the organisation                       | [Social]       | no       |
| labels            | Metadata for the individual contracts                       | [AddressLabel] | yes      |

### Social

| field name | description               | data type | required |
| ---------- | ------------------------- | --------- | -------- |
| platform   | Social platform           | string    | yes      |
| link       | Url to the social account | string    | yes      |

### AddressLabel

| field name  | description                                           | data type | required |
| ----------- | ----------------------------------------------------- | --------- | -------- |
| type        | Type of value to match on. Can be ergotree or address | string    | yes      |
| match_rule  | Regular expression to match                           | string    | yes      |
| label       | Short label identifying the contract                  | string    | yes      |
| description | Extra description for the contract                    | string    | no       |
| repo        | repo in the github organisation holding the contract  | string    | no       |

## JSON example

```json
{
  "organisation_name": "Spectrum Labs",
  "github": "https://github.com/spectrum-finance",
  "url": "https://spectrum.fi",
  "socials": [
    { "platform": "Telegram", "link": "Add tg link here" }
  ],
  "labels": [
    {
      "type": "ergotree",
      "match_rule": "[.*]d802d601b2a4730000d6029c73017e730205eb027303d195ed92b1a4730493b1db630872017305d804d603db63087201d604b2a5730600d60599c17204c1a7d606997e7307069d9c7e7205067e7308067e730906ededededed938cb27203730a0001730b93c27204730c927205730d95917206730ed801d607b2db63087204730f00ed938c7207017310927e8c7207020672067311909c7ec17201067e7202069c7e9a72057312069a9c7e8cb2720373130002067e7314067e72020690b0ada5d90107639593c272077315c1720773167317d90107599a8c7207018c72070273187319",
      "label": "Spectrum Buy Order V3",
      "description": "Proxy contract for setting a buy order on a native to token pair on Spectrum",
      "repo": "ergo-dex"
    },
    {
      "type": "ergotree",
      "match_rule": "[.*]d804d601b2a4730000d6027301d6037302d6049c73037e730405eb027305d195ed92b1a4730693b1db630872017307d806d605db63087201d606b2a5730800d607db63087206d608b27207730900d6098c720802d60a95730a9d9c7e997209730b067e7202067e7203067e720906edededededed938cb27205730c0001730d93c27206730e938c720801730f92720a7e7310069573117312d801d60b997e7313069d9c720a7e7203067e72020695ed91720b731492b172077315d801d60cb27207731600ed938c720c017317927e8c720c0206720b7318909c7e8cb2720573190002067e7204069c9a720a731a9a9c7ec17201067e731b067e72040690b0ada5d9010b639593c2720b731cc1720b731d731ed9010b599a8c720b018c720b02731f7320",
      "label": "Spectrum Sell Order V3",
      "description": "Proxy contract for setting a sell order on a native to token pair on Spectrum",
      "repo": "ergo-dex"
    }
  ]
}
```
