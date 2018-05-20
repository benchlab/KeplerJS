<p align="center">
  <img src="https://github.com/benchlab/benchx-media/raw/master/benos-logo.png" width="300px" alt="benOS Logo"/>
</p> <br>

# KeplerJS

KeplerJS Javascript library for interacting with Bench Network's Kepler Service.

## What Does KeplerJS Do?
KeplerJS provides a library for the following:

- Creating / Retreiving Kepler [Account](https://github.com/benchlab/keplar) ID Objects <br>
- Creating / Retreiving Kepler [Explorer](https://github.com/benchlab/explorer) ID Objects <br>
- Creating / Retreiving Kepler [Neutron](https://github.com/benchlab/neutron) ID Objects <br>
- Creating / Retreiving Kepler [Website](https://github.com/benchlab/designate) ID Objects <br>
- Creating / Retreiving Kepler [Nova](https://github.com/benchlab/nova) ID Objects <br>
- Creating / Retreiving Kepler [Aero](https://github.com/benchlab/aero) ID Objects <br>

## Quick start

Using npm to include `keplerjs` in your own project:
```shell
npm install --save keplerjs
```

You can also use yarn to include `keplerjs` in your own project:
```shell
yarn add keplerjs
```

For websites and web browser, we utilize Bower. It exports a variable `KeplerJS`. The example below assumes you have `keplerjs.js` relative to your html file.

```html
<script src="keplerjs.js"></script>
<script>console.log(KeplerJS);</script>

```

## Add KeplerJS To Your Application

### To use KeplerJS within your next Bench-based dApp or application, follow these instructions:
1. Install it using yarn:
  ```shell
  yarn install keplerjs
  ```

2. Regular Import of KeplerJS
  ```js
  var KeplerJS = require('keplerjs');
  ```
{IF ES6}
3. ES6 Import of KeplerJS
  ```js
  import KeplerJS from 'keplerjs';
  ```

### Use KeplerJS Inside Your Website
1. Install it using [bower](http://bower.io):

  ```shell
  bower install keplerjs
  ```

2. Include it in your webpage:

  ```html
  <script src="./bower_components/keplerjs/keplerjs.js"></script>
  <script>console.log(KeplerJS);</script>
  ```

If you don't want to use install Bower, you can copy built JS files from the [Kepler-Bower Repository](https://github.com/benchlab/kepler-bower).

### Add KeplerJS Inside Your Website With CDNJS
1. Add the follow code to your root HTML file using the [Kepler-CDNJS-Library](https://cdnjs.com/libraries/keplerjs)

  ```html
  <script src="https://cdnjs.cloudflare.com/ajax/libs/benchlabs/1.0.0/keplerjs.js"></script>
  <script>console.log(KeplerJS);</script>
  ```

### To Develop On KeplerJS
1. Clone via the KeplerJS GitHub Repository
  ```shell
  git clone https://github.com/benchlab/keplerjs.git
  ```

2. Yarn install all KeplerJS Dependencies
  ```shell
  cd keplerjs
  yarn
  ```

## KeplerJS Reference
Below is information related to the usage of KeplerJS within your application. <br>

### Kepler Account UID Attributes
***Attributes:*** <br>
**Key:** `uuid`: Key value UUID for KeplerAccount ID Object, generated via `KeplerUUID` library. <br>
`account_uuid`: RFC-compliant v4 Account UUID for KeplerAccount ID Object, generated via `KeplerUUID` library. <br>
`id`: SHA256 hash of the `account_uuid` <br>
`wallet_addr_sec`: ed25519 secret key, derived from seed, which derives from `id` <br>
`wallet_addr_uni`: ed25519 universal key, derived from `wallet_addr_sec` <br>
`sec_key`: ed25519 secret key, derived from `wallet_addr_sec`, which derives from `id` <br> 
`uni_key`: ed25519 universal key, derived from `sec_key` <br> 
`nonce`: SALSA20 hash of uni_key <br> 
`hex_key`: BASE64 of Account ID Object UUID Key <br> 
`klob`: klobs are blob data related to the KeplerAccount ID Object UUID. This could be the benOS-related node that the Account UUID was generated from. Klob-based data generated with Account UUIDs can differ, depending on the circumstances surrounding the generation of the Account UUID. <br>
`klob`>`uuid`: Reference of the `uuid`  <br>
`klob`>`account_uuid`: Reference of the `account_uuid` <br>
`klob`>`time_created`: Time that the KeplerAccount ID Object was created <br>
`klob`>`benchx_uuid`: Only included and auto-generated, if generated via benOS-based device <br>

### Creating New KeplerAccount ID Object
new KeplerAccount(keplerUuid, accountUuid, accountId, walletAddrUni, walletAddrSec, uniKey, secKey, nonce, hexKey, klob) <br>
**Source:** ***node_modules/keplerbase/src/kepleraccount.js, line 17*** <br>

| Parameter | Type | Description |
|----------|---------|-------------|
| `keplerUuid` | string | Key value UUID for KeplerAccount ID Object |
| `accountUuid` | string | RFC-compliant v4 Account UUID for KeplerAccount ID Object |
| `accountId` | string | SHA256 hash of the `accountUuid` |
| `walletAddrSec` | string | ed25519 secret key, derived from seed, which derives from `accountId` |
| `walletAddrUni` | string | ed25519 universal key, derived from `walletAddrSec`|
| `secKey` | string | ed25519 secret key, derived from `walletAddrSec`, which derives from `accountId` |
| `uniKey` | string | ed25519 universal key, derived from `secKey` |
| `nonce` | string | Salsa20 nonce to protect from replays |
| `hexKey` | string | BASE64 of Account ID Object UUID Key  |
| `klob` | array | Kepler blob data related to KeplerAccount ID Object creation |
| `klob` > `keplerUuid` | array-element | Reference of the `keplerUuid` |
| `klob` > `accountUuid` | array-element | Reference of the `accountUuid` |
| `klob` > `time_created` | array-element | Time that the KeplerAccount ID Object was created |
| `klob` > `benchx_uuid` | array-element | Only included and auto-generated, if generated via benOS-based device |


Example Response via `console.log`
```
uuid: 2fd305ea-912c-405b-bfed-7d98143d0d56 // Key value UUID for KeplerAccount ID Object, generated via `KeplerUUID` library.
account_uuid: e4f48839-db29-47c4-abc9-7e33dada1858 // RFC-compliant v4 Account UUID for KeplerAccount ID Object, generated via `KeplerUUID` library.
id: 3ebb0942f24e02c2f69d7d79bf4ace02645d42d247336738c0777084826aaac0 // SHA256 hash of the `account_uuid` 
wallet_addr_sec: upzjknOyoc8EzJSIk/6jyOGLIrS4mpml/hcQoMOaNDE= // ed25519 secret key, derived from seed, which derives from `id` 
wallet_addr_uni: VYBioijzebrLwDX2K8wkMRLD98iRjbatQV4guXw2iDw= // ed25519 universal key, derived from `wallet_addr_sec`
sec_key: ThO6DslXOwZucznK/E0jjUNYR3tw2sySjgW6HXjmd6wkapkxYvMLH7XCFamlYgd4K2YZ/1WA/wRD6Pb/Pc9nLg== // ed25519 secret key, derived from `wallet_addr_sec`, which derives from `id`
uni_key: JGqZMWLzCx+1whWppWIHeCtmGf9VgP8EQ+j2/z3PZy4= // ed25519 universal key, derived from `sec_key`
nonce: 0fef761a1f95b18948412e521a37ee49369d46b0025dd71cfd5d246c9744f3d1294eeab44acb0f320352f82a29dca4a2f503468098a99f4496c997fbe891846a // based on uni_key
hex_key: MmZkMzA1ZWEtOTEyYy00MDViLWJmZWQtN2Q5ODE0M2QwZDU2 // BASE64 of Account ID Object UUID Key 
klob: { 
uuid: 2fd305ea-912c-405b-bfed-7d98143d0d56, // Reference of the `uuid` 
account_uuid: 'e4f48839-db29-47c4-abc9-7e33dada1858', // Reference of the `account_uuid`
time_created: '2018-05-20T07:11:22.526Z', // Time that the KeplerAccount ID Object was created
benchx_uuid: 'b33a4dcd-7057-4618-a635-9ad476cb45c3' // Only included and auto-generated, if generated via benOS-based device
}
```

## KeplerJS Testing
To run all tests:
```shell
gulp test
```

To run a specific set of tests:
```shell
gulp test:node
gulp test:browser
```

# What Is benOS
[benOS](https://github.com/benchlab/benos) is a decentralized operating system, originally based on Linux, uses some design strategies from [RedoxOS](https://github.com/redox-os) and even some design concepts from [OpenStack](https://github.com/openstack), [Ethereum](https://github.com/ethereum/go-ethereum) and [EOS](https://github.com/eosio). Although we utilize some of their design strategies, benOS is completely custom from a codebase perspective. 

benOS has many components that make the wheels turn. Below are a list of those components:

## Other benOS Network Components
[Nova](https://github.com/benchlab/nova) - Global Decentralized Hypervisor For The Bench Network <br>
[Kepler](https://github.com/benchlab/kepler) - Global Decentralized Identity Management For The Bench Network <br>
  - [KeplerJS](https://github.com/benchlab/keplerjs) - Javascript Library For Working With Kepler Service <br>
  - [KeplerUUID](https://github.com/benchlab/kepleruuid) - Javascript Library For Creating Kepler UUIDs<br>
  - [Kepler-CLI](https://github.com/benchlab/kepler-cli) - CLI For Generating Kepler ID Sets<br>
  - [KeplerBase](https://github.com/benchlab/keplerbase) - Base Javascript Library For The Kepler Service<br>
  
[Designate](https://github.com/benchlab/designate) - Global Decentralized Naming Service For The Bench Network <br>
[Flutter](https://github.com/benchlab/flutter) - Global Decentralized Image Service For The Bench Network <br>
[Neutron](https://github.com/benchlab/neutron) - Global Network Creation & Management For The Bench Network <br>
  - [BenchCore](https://github.com/benchlab/BenchCore) - Core Decentralized Network Component For The Bench Network <br>
  - [BenchChain](https://github.com/benchlab/BenchChain) - Neutron's RootChain On The Bench Network <br>

[Aero](https://github.com/benchlab/aero) - Global Object Storage Distributor & Manager For The Bench Network <br>
[Explorer](https://github.com/benchlab/explorer) - Global dApp Distributor, Manager and Viewer For The Bench Network <br>
[benFS](https://github.com/benchlab/benFS) - benOS FileSystem <br>
[dappJS](https://github.com/benchlab/dappjs) - dApp Development Kit For The Bench Network <br>
[Mercury](https://github.com/benchlab/mercury) - benOS Graphical User Interface <br>
[Asteroid](https://github.com/benchlab/go-asteroid) - benOS Native Programming Language <br>
[Meteor](https://github.com/benchlab/meteor) - benOS Native IDE for dApp Development <br>
<br>

## benOS Core Components
[benOS-Microkernel](https://github.com/benOS-Microkernel) - benOS Microkernel <br>
[benOS-Bootloader](https://github.com/benchlab/benOS-Bootloader) - benOS Bootloader <br>
[ParseArgs](https://github.com/benchlab/parseargs) - benOS-based Argument Parsing  <br>
[X](https://github.com/benchlab/X) - benOS Graphical User Interface <br>

**NOTE:** ***There are other pieces under development as well, as our development team grows.*** 

## CREDITS AND ATTRIBUTES
benOS may use software from other open source libraries. For a full list of software credits and acknowledgements, please visit [https://github.com/benchlab/benOS/blob/master/ATTRIBUTES.md](https://github.com/benchlab/benOS/blob/master/ATTRIBUTES.md). The original LICENSE or LICENSES for the originating software(s) and library or libraries that were used to create `KeplerJS` are still active, although, considering this Bench software and the softwares and/or libraries/packages it is `imported` into may be used to issue illegal securities, the BENCH LICENSE is activated for this purpose. This does not take away the credits, disable the originating LICENSE or in any way disown the original creation, creators, developers or organizations that originally developed many of the libraries used throughout Bench's large array of software libraries packaged together for the purposes of building a decentralized operating system (benOS)

## VERSION
1.0.0

## LICENSE
BENCH LICENSE<br>
For KeplerJS
<br><br>
Copyright (c) 2018 Bench Computer, Inc. <legal@benchx.io>
<br><br>
Permission to use, copy, modify, and distribute this blockchain-related
software or blockchain-based software for any purpose with or without 
fee is hereby granted, provided that the above copyright notice and this 
permission notice appear in all copies.

THE USAGE OF THIS BLOCKCHAIN-RELATED OR BLOCKCHAIN-BASED SOFTWARE WITH THE
PURPOSE OF CREATING ICOS OR "INITIAL COIN OFFERINGS", UNREGISTERED SECURITIES 
SPECIFICALLY IN THE UNITED STATES OR IN OTHER COUNTRIES THAT HAVE A LEGAL 
FRAMEWORK FOR SECURITIES, IS PROHIBITED. BENCH FOUNDATION, LLC RESERVES THE 
RIGHT TO TAKE LEGAL ACTION AGAINST ANY AND ALL COMPANIES OR INDIVIDUALS WHO
USE THIS BLOCKCHAIN-RELATED OR BLOCKCHAIN-BASED SOFTWARE FOR THE PURPOSE OF 
DISTRIBUTING CRYPTOCURRENCIES WHERE THOSE CRYPTOCURRENCIES AND THEIR METHOD
OF DISTRIBUTION ARE IN DIRECT VIOLATION OF UNITED STATES SECURITIES LAWS. 
IF A GOVERNMENT BODY TAKES ACTION AGAINST ANY USERS, DEVELOPERS, MARKETERS,
ORGANIZATIONS, FOUNDATIONS OR ANY PROFESSIONAL ENTITY WHO CHOOSES TO UTILIZE
THIS SOFTWARE FOR THE DISTRIBUTION OF ILLEGAL SECURITIES, BENCH COMPUTER INC.
WILL NOT BE HELD LIABLE FOR ANY ACTIONS TAKEN BY THE USERS, DEVELOPERS, MARKETERS,
ORGANIZATIONS, FOUNDATIONS OR ANY PROFESSIONAL ENTITIES WHO CHOOSE TO DO SO.

UNITED STATES SECURITIES VIOLATIONS SPECIFICALLY REFER TO ANY VIOLATIONS OF
SECTION 10(b) OF THE SECURITIES EXCHANGE ACT OF 1934 [15 U.S.C. § 78j(b)] AND
RULE 10b-5(b) PROMULGATED THEREUNDER [17 C.F.R. § 240.10b-5(b)], AND
SECTIONS 5(a), 5(c), and 17(a)(2) OF THE SECURITIES ACT OF 1933 [15 U.S.C.
§§ 77e(a), 77e(c), and 77q(a)(2)]; BY MAKING USE OF ANY MEANS OR INSTRUMENTS
OF TRANSPORTATION OR COMMUNICATION IN INTERSTATE COMMERCE OR OF THE MAILS TO
SELL THROUGH THE USE OR MEDIUM OF ANY WRITTEN CONTRACT, OFFERING DOCUMENT,
PROSPECTUS, WHITEPAPER, OR OTHERWISE, ANY SECURITY AS TO WHICH NO REGISTRATION
STATEMENT WAS IN EFFECT. OR FOR THE PURPOSE OF SALE OR DELIVERY AFTER SALE,
CARRYING OR CAUSING TO BE CARRIED THROUGH THE MAILS OR IN INTERSTATE COMMERCE,
BY MEANS OR INSTRUMENTS OF TRANSPORTATION OR COMMUNICATION IN INTERSTATE
COMMERCE OR OF THE MAILS TO OFFER TO SELL OR OFFER TO BUY THROUGH THE USE OR 
MEDIUM OF ANY WRITTEN CONTRACT, OFFERING DOCUMENT, PROSPECTUS, WHITEPAPER,
OR OTHERWISE, SECURITIES AS TO WHICH NO REGISTRATION STATEMENT HAS BEEN FILED.

OUTSIDE OF THESE LEGAL REQUIREMENTS, THIS SOFTWARE IS PROVIDED "AS IS" AND 
THE AUTHOR DISCLAIMS ALL WARRANTIES WITH REGARD TO THIS SOFTWARE INCLUDING 
ALL IMPLIED WARRANTIES OF MERCHANTABILITY AND FITNESS. IN NO EVENT SHALL 
THE AUTHOR BE LIABLE FOR ANY SPECIAL, DIRECT, INDIRECT, OR CONSEQUENTIAL 
DAMAGES OR ANY DAMAGES WHATSOEVER RESULTING FROM LOSS OF USE, DATA OR PROFITS, 
WHETHER IN AN ACTION OF CONTRACT, NEGLIGENCE OR OTHER TORTIOUS ACTION, 
ARISING OUT OF OR IN CONNECTION WITH THE USE OR PERFORMANCE OF THIS SOFTWARE.





