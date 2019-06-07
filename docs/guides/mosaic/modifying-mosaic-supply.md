---
id: modifying-mosaic-supply
title: Modifying mosaic supply
---
Did you register a [mosaic](../../built-in-features/mosaic.md) with supplyMutable option set to true? In that case, you can increase or decrease your mosaic available supply following this guide.

## Prerequisites

- Finish [creating a mosaic guide](./creating-a-mosaic.md)
- NEM2-SDK or CLI
- A text editor or IDE
- An account with XEM
- Have registered a supply mutable mosaic

## Let’s get into some code

If you have followed the previous guide, right now you should own a `supply mutable` mosaic.

Increase to `2.000.000` the initial supply. Sign and announce a [mosaic supply change transaction](../../built-in-features/mosaic.md#mosaicsupplychangetransaction).

<!--DOCUSAURUS_CODE_TABS-->
<!--TypeScript-->
```js
const transactionHttp = new TransactionHttp('http://localhost:3000');

const privateKey = process.env.PRIVATE_KEY as string;
const account = Account.createFromPrivateKey(privateKey, NetworkType.MIJIN_TEST);

const mosaicID = new MosaicId('foo:token');

const mosaicSupplyChangeTransaction = MosaicSupplyChangeTransaction.create(
    Deadline.create(),
    mosaicID,
    MosaicSupplyType.Increase,
    UInt64.fromUint(2000000),
    NetworkType.MIJIN_TEST);

const signedTransaction = account.sign(mosaicSupplyChangeTransaction);

transactionHttp
    .announce(signedTransaction)
    .subscribe(x=> console.log(x), err => console.error(err));
```

<!--JavaScript-->
```js
const transactionHttp = new TransactionHttp('http://localhost:3000');

const privateKey = process.env.PRIVATE_KEY;
const account = Account.createFromPrivateKey(privateKey, NetworkType.MIJIN_TEST);

const mosaicID = new MosaicId('foo:token');

const mosaicSupplyChangeTransaction = MosaicSupplyChangeTransaction.create(
    Deadline.create(),
    mosaicID,
    MosaicSupplyType.Increase,
    UInt64.fromUint(2000000),
    NetworkType.MIJIN_TEST);

const signedTransaction = account.sign(mosaicSupplyChangeTransaction);

transactionHttp
    .announce(signedTransaction)
    .subscribe(x=> console.log(x), err => console.error(err));
```

<!--Java-->
```java
    // Replace with private key
    final String privateKey = "";

    final Account account = Account.createFromPrivateKey(privateKey, NetworkType.MIJIN_TEST);

    // Replace with mosaic id
    final MosaicId mosaicId = new MosaicId("foo:token"); // replace with mosaic full name

    MosaicSupplyChangeTransaction mosaicSupplyChangeTransaction = MosaicSupplyChangeTransaction.create(
        new Deadline(2, ChronoUnit.HOURS),
        mosaicId,
        MosaicSupplyType.INCREASE,
        BigInteger.valueOf(2000000),
        NetworkType.MIJIN_TEST
    );

    final SignedTransaction signedTransaction = account.sign(mosaicSupplyChangeTransaction);

    final TransactionHttp transactionHttp = new TransactionHttp("http://localhost:3000");

    transactionHttp.announce(signedTransaction).toFuture().get();
```
<!--END_DOCUSAURUS_CODE_TABS-->

## What’s next?

Decrease your mosaic supply by changing `MosaicSupplyType.Increase` for `MosaicSupplyType.Decrease`.
