# pawtils

This repository contains several utils to work with the cryptocurrency [Paw](https://paw.digital/) inside the Browser and Node.

### Demo:
 - [Browser Wallet](https://maierfelix.github.io/pawtils/example/wallet.html)
 - [Vanity Address Generator](https://maierfelix.github.io/pawtils/example/vanity-address.html)

### Documentation:
The documentation is auto-generated and can be found [here](https://maierfelix.github.io/pawtils/docs).

### Installation:
Package installation:
````
npm install pawtils
````
Browser installation:
````html
<script src="https://unpkg.com/pawtils/dist/index.iife.min.js"></script>
````

### Features:
 - RPC-based requests
 - Wallet generation (Seed, Address, Private and Public keys)
 - Mnemonic generation (BIP39)
 - QR code generation
 - Receiving and sending PAW
 - Several methods for querying data (Account balance, history etc.)
 - Proof-of-Work generation (CPU, GPU or NODE based)
 - AES PBKDF2 encryption/decryption

### Browser Example:
````html
<script src="https://unpkg.com/pawtils/dist/index.iife.min.js"></script>

<script>
(async() => {

  // Set API endpoint
  await pawtils.setAPIURL(`https://rpc2.paw.digital/`);

  // Generate random wallet
  const walletSeed = crypto.getRandomValues(new Uint8Array(32));
  const walletPrivateKey = pawtils.getPrivateKey(walletSeed);
  const walletPublicKey = pawtils.getPublicKey(walletPrivateKey);
  const walletAddress = pawtils.getAccountAddress(walletPublicKey);

  // Print wallet information
  console.log("Seed:", pawtils.bytesToHex(walletSeed));
  console.log("Address:", walletAddress);
  console.log("Private key:", pawtils.bytesToHex(walletPrivateKey));
  console.log("Public key:", pawtils.bytesToHex(walletPublicKey));

})();
</script>
````

### Node Example:
````js
const pawtils = require("pawtils");
const crypto = require("crypto").webcrypto;

(async () => {

  // Set API endpoint
  await pawtils.setAPIURL(`https://rpc2.paw.digital/`);

  // Generate random wallet
  const walletSeed = crypto.getRandomValues(new Uint8Array(32));
  const walletPrivateKey = pawtils.getPrivateKey(walletSeed);
  const walletPublicKey = pawtils.getPublicKey(walletPrivateKey);
  const walletAddress = pawtils.getAccountAddress(walletPublicKey);

  // Print wallet information
  console.log("Seed:", pawtils.bytesToHex(walletSeed));
  console.log("Address:", walletAddress);
  console.log("Private key:", pawtils.bytesToHex(walletPrivateKey));
  console.log("Public key:", pawtils.bytesToHex(walletPublicKey));

})();
````

### Inspired by:
 - [banotils](https://github.com/maierfelix/banotils)
