## Disclaimer
This is a work in progress. Expect breaking changes. The code has not been audited and therefore can not be considered secure.

## License
The current codebase is released under the [GPL 3.0 license](https://www.gnu.org/licenses/gpl-3.0.en.html)

## Develop
First, put these two configs into the configs folder:
`auth.config.json`:
```
{
  "clientId": «<YOUR_CLIENT_KEY>.apps.googleusercontent.com",
  "apiKey": "<YOUR_API_KEY>",
  "discoveryDocs": [
    "https://www.googleapis.com/discovery/v1/apis/drive/v3/rest",
    "https://www.googleapis.com/discovery/v1/apis/people/v1/rest"
  ],
  "scopes": {
    "drive": "https://www.googleapis.com/auth/drive.appdata",
    "contacts": "https://www.googleapis.com/auth/contacts.readonly"
  }
}
```

`app.config.json`:
```
{
  "claimHost":"http://localhost:5000",
  "masterCopy":"0x2f9Df93ebF334443c5719f01000f777749a3f99c",
  "factory":"0xBa051891B752ecE3670671812486fe8dd34CC1c8",
  "initialBlockMainnet":0,
  "initialBlockRinkeby":0,
  "initialBlockGoerli": 1176312,
  "initialBlockRopsten": 6420022,
  "initialBlockKovan": 13596489,
  "FACTORY_ADDRESS":"0xBa051891B752ecE3670671812486fe8dd34CC1c8",
  "infuraPk": "ecd43c9cd96e45ceb9131fba9b100b07",
  "defaultChainId": "4",
  "apiHostRinkeby": "https://rinkeby.linkdrop.io",
  "apiHostWalletRinkeby": "https://rinkeby-wallet-api-p2p.linkdrop.io",
  "apiHostMainnet": "https://mainnet.linkdrop.io",
  "apiHostWalletMainnet": "https://mainnet-wallet-api.linkdrop.io",
  "apiHostGoerli": "https://goerli.linkdrop.io",
  "apiHostWalletGoerli": "https://goerli-wallet-api.linkdrop.io",
  "openseaApiKey": "5cda77bcc2e64a679a1dd5ba1d38d9e2"
}
```

Get your `node` & `yarn` versions to:
`node v10.16.0`
`yarn 1.16.0`

You probably need to install `nvm` and search the commands to downgrade both.

### Setup google
Set up your google API at
https://developers.google.com/maps/documentation/directions/get-api-key

Then you need to run `yarn install` inside each package (contracts, sdk, apps/wallet, server).

Also run `yarn build` itself from root.

### Local server setup

Set your config file in `server/config/config.json`

```
{
  "CHAIN": "rinkeby",
  "INFURA_API_TOKEN": "###########",
  "RELAYER_PRIVATE_KEY": “########”###############,
  "GNOSIS_SAFE_MASTERCOPY_ADDRESS": "0xB945Bd4b447aF21C5B55eF859242829FBDc0bF0A",
  "PROXY_FACTORY_ADDRESS": "0x12302fE9c02ff50939BaAaaf415fc226C078613C",
  "MULTISEND_LIBRARY_ADDRESS": "0xD4B7B161E4779629C2717385114Bf78D612aEa72",
  "ENS_ADDRESS": "0xe7410170f87102df0055eb195163a03b7f2bff4a",
  "ENS_DOMAIN": "linkdrop.test",
  "LINKDROP_FACTORY_ADDRESS": "0xBa051891B752ecE3670671812486fe8dd34CC1c8",
  "CREATE_AND_ADD_MODULES_LIBRARY_ADDRESS": "0x1a56aE690ab0818aF5cA349b7D21f1d7e76a3d36",
  "LINKDROP_MODULE_MASTERCOPY_ADDRESS": "0xFBaD822d2E2710EEe31DC3298a8866ebaaBd9328",
  "MULTISEND_WITH_REFUND_ADDRESS": "0x51ed31B79911A12e63f45d51691A6129347f77eE",
  "RECOVERY_MODULE_MASTERCOPY_ADDRESS": "0xD3FaECC16097E96986F868220185F6470A3F1eA9",
  "JWT_SECRET": “randomsecret”,
  "COOKIE_SECRET": “randomsecret”,
  "SNARKART_REGISTER_URL": "https://cookies-api-test.snark.art/api/v1/users/new"
}
```

Then install mongodb and run `mongod` in root.

Then run `yarn server` from root to get the server running.

### Run the wallet locally
To run the wallet locally in your browser, go to`cd packages/apps/wallet` and run `yarn dev:server`.

### Set up google cloud to run the server

1. Set up a google compute engine
2. Upload the repo to this engine
3. `yarn install` in /server
4. `pm2 start --name amigo npm -- run server`
5. optionally `pm2 list` to get an overview on running processes
6. optionally `pm2 log amigo` to get the log
