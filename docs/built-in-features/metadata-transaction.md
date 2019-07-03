---
id: metadata-transaction
title: Metadata Transaction
---
Transfer transactions are used to send [mosaics](./mosaic.md) between two [accounts](./account.md). They can hold a messages of length `1023` characters.

![Transfer Transaction](/img/transfer-transaction.png "Transfer Transaction")

<p class="caption">Alice sends 10 prx:xpx to Bob</p>

<div class="info">

**Note**

It is possible to send mosaics to any valid address even if the address has not previously participated in any transaction. If nobody owns the private key of the recipient’s account, the funds are most likely lost forever.

</div>

## Guides

- [Sending a transfer transaction](../guides/transaction/sending-a-transfer-transaction.md)

    Transfer [*mosaics*](./mosaic.md) and messages between two accounts.

- [Monitoring a transaction status](../guides/monitoring/monitoring-a-transaction-status.md)

    Make sure a [*transaction*](../protocol/transaction.md) gets included in the blockchain after being announced.

## Schemas

<div class="info">

**Note**

Configuration parameters are [editable](https://github.com/proximax-storage/catapult-server/blob/master/resources/config-network.properties) . Public network configuration may differ.

</div>

### TransferTransaction

Announce a transfer transaction to send [mosaics](./mosaic.md) or messages between two [accounts](./account.md).

**Version**: 0x03

**Entity type**: 0x4154

**Inlines**:

- [Transaction](../protocol/transaction.md#transaction) or [EmbeddedTransaction](../protocol/transaction.md#embeddedtransaction)

**Property** |	**Type** |	**Description**
-------------|-----------|--------------------
recipient |	25 bytes (binary) |	The address of the recipient account.
messageSize |	uint16 |	The size of the attached message.
mosaicsCount |	uint8 |	The number of attached mosaics.
message |	array(byte, messageSize) |	The message type (0) and a payload of up to `1023` bytes.
mosaics |	array([UnresolvedMosaic](./mosaic.md#unresolvedmosaic), mosaicsCount) |	The different mosaic to be sent.

