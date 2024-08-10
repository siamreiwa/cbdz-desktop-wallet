# CBDZ Desktop Wallet

[![License](https://img.shields.io/badge/License-Apache%202.0-blue.svg)](https://opensource.org/licenses/Apache-2.0)

Cross-platform client for CBDZ(Symbol blockchain) to manage accounts, mosaics, namespaces, and issue transactions.

This project is a fork of [Symbol Desktop Wallet](https://github.com/symbol/desktop-wallet). 

We extend our gratitude to the original contributors for their valuable work.

## Installation

CBDZ Desktop Wallet is available for Mac, Windows, and as a web application.

1. Download CBDZ Desktop Wallet from the [releases section](https://github.com/siamreiwa/cbdz-desktop-wallet/releases).

2. Launch the executable file and follow the installation instructions.

3. Create a profile. Remember to save the mnemonic somewhere safe (offline).

## Building instructions

CBDZ CLI require **Node.js 16 LTS** and **npm install -g node-gyp@^7.1.0** to execute.

1. Clone the project.

```
git clone https://github.com/siamreiwa/cbdz-desktop-wallet
```

2. Install the dependencies.
```
cd cbdz-desktop-wallet
npm install
```

3. Start the development server.

```
npm run dev
```

4. Visit http://localhost:8080/#/ in your browser.

## Release
1. For local use, build CBDZ Wallet Electron app (only Electron version support Ledger wallets), default build for MacOS, Windows and Linux

<pre>
# to skip code signing
export CSC_IDENTITY_AUTO_DISCOVERY=false

npm run release
</pre>

2. Release for distribution: (Code signing for Apple builds - requires `Developer ID Certificate`)

    2.1 On a MacOS machine, download the zip file containing the app signing certificates (ask team)

    2.2 Extract the certificates and double click each one of them to add to the keychain (ask the team for private key password)

    2.3 Starting with MacOS 10.14.5, all signed applications by new `Developer ID Certificate` will need to be notarized. This is an automated step in the process. You'll need to enable notarization by setting the following env vars.

    <pre>
    export DESKTOP_APP_NOTARIZE=true
    export DESKTOP_APP_APPLE_ID=VALID_APPLE_DEV_ID
    export DESKTOP_APP_APPLE_PASSWORD=VALID_APPLE_DEV_PASSWORD
    export DESKTOP_APP_APPLE_TEAM_ID=VALID_APPLE_TEAM_ID
    </pre>

    2.4 Enable auto discovery for code signing process to pick up the certificates from the keychain

    <pre>export CSC_IDENTITY_AUTO_DISCOVERY=true</pre>

    2.5 Run release
    <pre>npm run release</pre>

    2.6 Validate if the app is signed with a `Developer ID Certificate` and notarized

    <pre>spctl -a -t exec -v ./release/mac/CBDZ\ Wallet.app
    # Output(Success): ./release/mac/CBDZ Wallet.app: accepted source=Notarized Developer ID
    # Output(Failure): ./release/mac/CBDZ Wallet.app: rejected source=Unnotarized Developer ID
    </pre>

## Getting help

Use the following available resources to get help:

- [Symbol Documentation][docs]
- If you found a bug, [open a new issue][issues]

## Contributing

Contributions are welcome and appreciated.
Check [CONTRIBUTING](CONTRIBUTING.md) for information on how to contribute.

## License

(C) Siam Reiwa (2020) Co., Ltd. 2024

Licensed under the [Apache License 2.0](LICENSE)

[self]: https://github.com/siamreiwa/cbdz-desktop-wallet
[docs]: https://docs.symbolplatform.com
[issues]: https://github.com/siamreiwa/cbdz-desktop-wallet/issues
