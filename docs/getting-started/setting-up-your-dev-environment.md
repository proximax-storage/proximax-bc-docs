---
id: setting-up-your-dev-environment
title: Setting up your development environment
---
This first guide will walk you through the step by step process of how to access the test network for your development and the necessary tools that can be used to view it.

## Connecting to Sirius-Chain Test Network
![Sirius-Chain Layer](/img/four-layer-architecture-basic.png "Sirius-Chain Layer")

For learning purposes, you are going to use the existing Sirius-Chain Test network.

```
http://bctestnet1.xpxsirus.io:3000
http://bctestnet2.xpxsirus.io:3000
```

######
1. Check if you can get the first block information:

```
$> curl http://bctestnet1.xpxsirus.io:3000/block/1
```

## Creating a test account
An account is a key pair (private and public key) associated to a mutable state stored in the Sirius-Chain. In other words, you have a deposit box on the blockchain, which only you can modify with your key pair. As the name suggests, the private key has to be kept secret at all times. Anyone with access to the private key, ultimately has control over the account.

The **public key** is cryptographically derived from the private key. It would take millions of years to do the reverse process and therefore, the public key is safe to be shared.

Finally, the account address is generated with the public key, following the Sirius-Chain protocol. Share this address instead of the public key, as it contains more information, such as a validity check or which network it uses (public, testnet or private).

[XPX2-CLI](../client/overview.md) conveniently allows you to perform the most commonly used commands from your terminal i.e. using it to interact with the blockchain, setting up an account, sending funds, etc.

1. Install XPX2-CLI using `npm`.

```
$> sudo npm install --global xpx2-cli
```

2. Create an account with the command line tool.

```
$> xpx2-cli account generate --network PRIVATE_TEST --save --url http://bctestnet1.xpxsirius.io:3000
```

The `network flag` is set to PUBLIC_TEST. Test network is an alternative Sirius-Chain used for development and testing purposes.

Use `save flag` to store the account on your computer. XPX2-CLI uses stored account to sign the transactions that you start.

3. You should be able to see the following lines in your terminal, containing the account credentials:

> New Account: VCVG35-ZSPMYP-L2POZQ-JGSVEG-RYOJ3V-BNIU3U-N2E6 <br> Public Key: 33E0…6ED <br> Private Key: 0168…595

## What is XPX and how to get it?

The underlying cryptocurrency of the Sirius-Chain network is called **XPX**. Every action on the Sirius-Chain costs XPX, in order to provide an incentive for those who validate and secure the network.

Let’s use an account which already has XPX. We will need it to register the namespace and mosaic.

1. Open a terminal, and go to the directory where you have download Sirius-Chain Bootstrap Service.

```
$> cd  build/generated-addresses/
$> cat addresses.yaml
```
2. Under the section `nemesis_addresses`, you will find the key pairs which contain XPX.
3. Load the first account as a profile in XPX2-CLI.
```
$> xpx2-cli profile create

Introduce network type (PRIVATE_TEST, PRIVATE, MAIN_NET, TEST_NET): PRIVATE_TEST
Introduce your private key: 41************************************************************FF
Introduce Sirius-Chain Node URL. (Example: http://localhost:3000): http://localhost:3000
Insert profile name (blank means default and it could overwrite the previous profile):
```
## Setting up the development environment
It is time to choose a programming language. Pick the one you feel most comfortable with, or follow your project requirements.

Create a folder for your new project and run the instructions for the selected language.

<!--DOCUSAURUS_CODE_TABS-->
<!--TypesSript-->

1. Create a `package.json` file. The minimum required Node.js version is 8.9.X.
```
$> npm init
```
2. Install tsjs-xpx-chain-sdk and rxjs library.
```
$> npm install tsjs-xpx-chain-sdk rxjs
```
<!--END_DOCUSAURUS_CODE_TABS-->

3. tsjs-xpx-chain-sdk is build with TypeScript language. It is recommended to use TypeScript instead of JavaScript when building applications for Sirius-Chain.

Make sure you have at least version 2.5.X installed.
```
$> sudo npm install --global typescript
$> typescript --version
```

4. Use ts-node to execute TypeScript files with node.
```
$> sudo npm install --global ts-node
```