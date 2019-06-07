---
id: asking-for-mosaics-with-aggregate-bonded-transaction
title: Asking for mosaics with aggregate-bonded transaction
---
Ask an account to send you funds using an [aggregate bonded transaction](../../built-in-features/aggregate-transaction.md).

## Prerequisites

- Finish [creating an escrow with aggregate bonded transaction guide](./creating-an-escrow-with-aggregate-bonded-transaction.md)
- A text editor or IDE
- An account with XEM

## Let’s get into some code

![Aggregate asking for mosaics](/img/aggregate-asking-for-mosaics.png "Aggregate asking for mosaics")

<p class=caption>Asking for mosaics with an aggregate bonded transaction</p>

Alice wants to ask Bob for 20 XEM.

1. Set up both Alice’s and Bob’s accounts.

<!--DOCUSAURUS_CODE_TABS-->
<!--TypesSript-->
```js
const nodeUrl = 'http://localhost:3000';
const transactionHttp = new TransactionHttp(nodeUrl);
const listener = new Listener(nodeUrl);

const alicePrivateKey = process.env.ALICE_PRIVATE_KEY as string;
const aliceAccount = Account.createFromPrivateKey(alicePrivateKey, NetworkType.MIJIN_TEST);

const bobPublicKey = 'F82527075248B043994F1CAFD965F3848324C9ABFEC506BC05FBCF5DD7307C9D';
const bobAccount = PublicAccount.createFromPublicKey(bobPublicKey, NetworkType.MIJIN_TEST);
```
<!--JavaScript-->
```js
const nodeUrl = 'http://localhost:3000';
const transactionHttp = new TransactionHttp(nodeUrl);
const listener = new Listener(nodeUrl);

const alicePrivateKey = process.env.ALICE_PRIVATE_KEY;
const aliceAccount = Account.createFromPrivateKey(alicePrivateKey, NetworkType.MIJIN_TEST);

const bobPublicKey = 'F82527075248B043994F1CAFD965F3848324C9ABFEC506BC05FBCF5DD7307C9D';
const bobAccount = PublicAccount.createFromPublicKey(bobPublicKey, NetworkType.MIJIN_TEST);
```
<!--Java-->
```java
import java.math.BigInteger;
import java.net.MalformedURLException;
import java.util.Arrays;
import java.util.Collections;
import java.util.concurrent.ExecutionException;

import static java.time.temporal.ChronoUnit.HOURS;

class AskingForMosaicsWithAggregateBondedTransaction {

    @Test
    void askingForMosaicsWithAggregateBondedTransaction() throws ExecutionException, InterruptedException, MalformedURLException {

        // Replace with a Alice's private key
        final String alicePrivateKey = "";

        // Replace with a Bob's public key
        final String bobPublicKey = "";

        final Account aliceAccount = Account.createFromPrivateKey(alicePrivateKey, NetworkType.MIJIN_TEST);
        final PublicAccount bobPublicAccount = PublicAccount.createFromPublicKey(bobPublicKey, NetworkType.MIJIN_TEST);
```

<!--END_DOCUSAURUS_CODE_TABS-->

2. Alice creates an aggregate bonded transaction with two inner transactions:

<div class=cap-alpha-ol>

1. Define the first inner [transfer transaction](../../built-in-features/transfer-transaction.md#transfertransaction):

</div>

- message: “message reason” (custom, but not empty)
- receiver: Bob address
- signer: Alice

<!--DOCUSAURUS_CODE_TABS-->

<!--TypeScript-->
```js
const transferTransaction1 = TransferTransaction.create(
    Deadline.create(),
    bobAccount.address,
    [],
    PlainMessage.create('send me 20 XEM'),
    NetworkType.MIJIN_TEST);
```

<!--JavaScript-->
```js
const transferTransaction1 = TransferTransaction.create(
    Deadline.create(),
    bobAccount.address,
    [],
    PlainMessage.create('send me 20 XEM'),
    NetworkType.MIJIN_TEST);
```

<!--Java-->
```java
    final TransferTransaction transferTransaction1 = TransferTransaction.create(
        Deadline.create(2, HOURS),
        bobPublicAccount.getAddress(),
        Collections.emptyList(),
        PlainMessage.create("send me 20 XEM"),
        NetworkType.MIJIN_TEST
    );
```

<!--END_DOCUSAURUS_CODE_TABS-->

<div class=cap-alpha-ol>

2. Define the second inner [transfer transaction](../../built-in-features/transfer-transaction.md#transfertransaction):

</div>

- message: empty
- receiver: Alice address
- mosaics: 20 XEM
- signer: Bob

<!--DOCUSAURUS_CODE_TABS-->

<!--TypeScript-->
```js
const transferTransaction2 = TransferTransaction.create(
    Deadline.create(),
    aliceAccount.address,
    [XEM.createRelative(20)],
    EmptyMessage,
    NetworkType.MIJIN_TEST);
```

<!--JavaScript-->
```js
const transferTransaction2 = TransferTransaction.create(
    Deadline.create(),
    aliceAccount.address,
    [XEM.createRelative(20)],
    EmptyMessage,
    NetworkType.MIJIN_TEST);
```

<!--Java-->
```java
    final TransferTransaction transferTransaction2 = TransferTransaction.create(
        Deadline.create(2, HOURS),
        aliceAccount.getAddress(),
        Collections.singletonList(XEM.createRelative(BigInteger.valueOf(20))),
        PlainMessage.Empty,
        NetworkType.MIJIN_TEST
    );
```

<!--END_DOCUSAURUS_CODE_TABS-->

3. Wrap the defined transactions in an aggregate bonded transaction:

<!--DOCUSAURUS_CODE_TABS-->
<!--TypeScript-->
```js
const aggregateTransaction = AggregateTransaction.createBonded(
    Deadline.create(),
    [transferTransaction1.toAggregate(aliceAccount.publicAccount),
        transferTransaction2.toAggregate(bobAccount)],
    NetworkType.MIJIN_TEST);

const signedTransaction = aliceAccount.sign(aggregateTransaction);
```

<!--JavaScript-->
```js
const aggregateTransaction = AggregateTransaction.createBonded(
    Deadline.create(),
    [transferTransaction1.toAggregate(aliceAccount.publicAccount),
        transferTransaction2.toAggregate(bobAccount)],
    NetworkType.MIJIN_TEST);

const signedTransaction = aliceAccount.sign(aggregateTransaction);
```

<!--Java-->
```java
    final TransferTransaction transferTransaction2 = TransferTransaction.create(
        Deadline.create(2, HOURS),
        aliceAccount.getAddress(),
        Collections.singletonList(XEM.createRelative(BigInteger.valueOf(20))),
        PlainMessage.Empty,
        NetworkType.MIJIN_TEST
    );
```

<!--END_DOCUSAURUS_CODE_TABS-->

4. Alice signs the aggregate bonded transaction and announces it to the network, locking first 10 XEM.

<!--DOCUSAURUS_CODE_TABS-->
<!--TypeScript-->
```js
const lockFundsTransaction = LockFundsTransaction.create(
    Deadline.create(),
    XEM.createRelative(10),
    UInt64.fromUint(480),
    signedTransaction,
    NetworkType.MIJIN_TEST);

const lockFundsTransactionSigned = aliceAccount.sign(lockFundsTransaction);

listener.open().then(() => {

    transactionHttp
        .announce(lockFundsTransactionSigned)
        .subscribe(x => console.log(x), err => console.error(err));

    listener
        .confirmed(aliceAccount.address)
        .pipe(
            filter((transaction) => transaction.transactionInfo !== undefined
                && transaction.transactionInfo.hash === lockFundsTransactionSigned.hash),
            mergeMap(ignored => transactionHttp.announceAggregateBonded(signedTransaction))
        )
        .subscribe(announcedAggregateBonded => console.log(announcedAggregateBonded),
            err => console.error(err));
});
```

<!--JavaScript-->
```js
const lockFundsTransaction = LockFundsTransaction.create(
    Deadline.create(),
    XEM.createRelative(10),
    UInt64.fromUint(480),
    signedTransaction,
    NetworkType.MIJIN_TEST);

const lockFundsTransactionSigned = aliceAccount.sign(lockFundsTransaction);

listener.open().then(() => {

    transactionHttp
        .announce(lockFundsTransactionSigned)
        .subscribe(x => console.log(x), err => console.error(err));

    listener
        .confirmed(aliceAccount.address)
        .pipe(
            filter((transaction) => transaction.transactionInfo !== undefined
                && transaction.transactionInfo.hash === lockFundsTransactionSigned.hash),
            mergeMap(ignored => transactionHttp.announceAggregateBonded(signedTransaction))
        )
        .subscribe(announcedAggregateBonded => console.log(announcedAggregateBonded),
            err => console.error(err));
});
```

<!--Java-->
```java
    final SignedTransaction pullTransactionSigned = aliceAccount.sign(pullTransaction);

    // Creating the lock funds transaction and announce it
    final LockFundsTransaction lockFundsTransaction = LockFundsTransaction.create(
        Deadline.create(2, HOURS),
        XEM.createRelative(BigInteger.valueOf(10)),
        BigInteger.valueOf(480),
        pullTransactionSigned,
        NetworkType.MIJIN_TEST
    );

    final SignedTransaction lockFundsTransactionSigned = aliceAccount.sign(lockFundsTransaction);

    final TransactionHttp transactionHttp = new TransactionHttp("http://localhost:3000");

    transactionHttp.announce(lockFundsTransactionSigned).toFuture().get();

    System.out.println(lockFundsTransactionSigned.getHash());

    final Listener listener = new Listener("http://localhost:3000");

    listener.open().get();

    final Transaction transaction = listener.confirmed(aliceAccount.getAddress()).take(1).toFuture().get();

    transactionHttp.announceAggregateBonded(pullTransactionSigned).toFuture().get();
```

<!--END_DOCUSAURUS_CODE_TABS-->

<div class=info>

**Note**

The [listener implementation changes](../monitoring/monitoring-a-transaction-status.md#troubleshooting-monitoring-transactions-on-the-client-side) when used on the client side (e.g., Angular, React, Vue).

</div>

If all goes well, [Bob receives a notification](../monitoring/monitoring-a-transaction-status.md).

## What’s next?

Bob has not cosigned the transaction yet. Consider reading [signing announced aggregate bonded transactions](./signing-announced-aggregate-bonded-transactions.md) guide.

After receiving the transaction, Bob signs the `transaction hash` and announces the cosignature signed transaction.

As the aggregate bonded transaction has all the cosignatures required, it will be included in a block.
