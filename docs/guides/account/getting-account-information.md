---
id: getting-account-information
title: Getting account information
---
Get the public key and balance of an [account](../../built-in-features/account.md).

## Prerequisites

- Finish the [getting started section](../../getting-started/setting-up-workstation.md)
- Text editor or IDE
- XPX-Chain-SDK or CLI

## Let’s get into some code

The **public key** identifies your account publicly in the network. Your **address** is derived from it, which contains further information such as network and validity check.

Get more information about your account passing the address and network as a parameter.

<!--DOCUSAURUS_CODE_TABS-->
<!--TypesSript-->

```ts
const accountHttp = new AccountHttp('http://localhost:3000');
const address = Address.createFromRawAddress('SD5DT3-CH4BLA-BL5HIM-EKP2TA-PUKF4N-Y3L5HR-IR54');

accountHttp
    .getAccountInfo(address)
    .subscribe(accountInfo => console.log(accountInfo), err => console.error(err));
```

<!--JavaSript-->
```js
const accountHttp = new AccountHttp('http://localhost:3000');
const address = Address.createFromRawAddress('SD5DT3-CH4BLA-BL5HIM-EKP2TA-PUKF4N-Y3L5HR-IR54');

accountHttp
    .getAccountInfo(address)
    .subscribe(accountInfo => console.log(accountInfo), err => console.error(err));
```

<!--bash-->
```sh
xpx-cli account info --address SD5DT3-CH4BLA-BL5HIM-EKP2TA-PUKF4N-Y3L5HR-IR54
```

<!--Java-->
```java
    final AccountHttp accountHttp = new AccountHttp("http://localhost:3000");

    // Replace with address
    final String address = "SD5DT3-CH4BLA-BL5HIM-EKP2TA-PUKF4N-Y3L5HR-IR54";

    final AccountInfo accountInfo = accountHttp.getAccountInfo(Address.createFromRawAddress(address)).toFuture().get();

    System.out.println(accountInfo);
```

<!--END_DOCUSAURUS_CODE_TABS-->

Can you determine the account’s public key? Which was the first block where this account appeared?

### Checking account’s balance

The balance is the amount of the different mosaics owned by the account. How many different mosaics does your account own?

<!--DOCUSAURUS_CODE_TABS-->
<!--TypesSript-->

```ts
const url = 'http://localhost:3000';
const accountHttp = new AccountHttp(url);
const mosaicHttp = new MosaicHttp(url);
const namespaceHttp = new NamespaceHttp(url);
const mosaicService = new MosaicService(accountHttp, mosaicHttp, namespaceHttp);

const address = Address.createFromRawAddress("SD5DT3-CH4BLA-BL5HIM-EKP2TA-PUKF4N-Y3L5HR-IR54");

mosaicService
    .mosaicsAmountViewFromAddress(address)
    .pipe(
        mergeMap((_) => _)
    )
    .subscribe(mosaic => console.log('You have', mosaic.relativeAmount(), mosaic.fullName()),
        err => console.error(err));
```

<!--JavaSript-->
```js
const url = 'http://localhost:3000';
const accountHttp = new AccountHttp(url);
const mosaicHttp = new MosaicHttp(url);
const namespaceHttp = new NamespaceHttp(url);
const mosaicService = new MosaicService(accountHttp, mosaicHttp, namespaceHttp);

const address = Address.createFromRawAddress("SD5DT3-CH4BLA-BL5HIM-EKP2TA-PUKF4N-Y3L5HR-IR54");

mosaicService
    .mosaicsAmountViewFromAddress(address)
    .pipe(
        mergeMap((_) => _)
    )
    .subscribe(mosaic => console.log('You have', mosaic.relativeAmount(), mosaic.fullName()),
        err => console.error(err));
```

<!--bash-->
```sh
xpx-cli account info --address SD5DT3-CH4BLA-BL5HIM-EKP2TA-PUKF4N-Y3L5HR-IR54
```

<!--END_DOCUSAURUS_CODE_TABS-->

## What’s next?

Retrieve the balance by only [filtering the prx:xpx](https://www.learnrxjs.io/operators/filtering/filter.html) amount.
