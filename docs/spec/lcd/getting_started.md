## Getting Started

To start a rest server, we need to specify the following parameters:

| Parameter   | Type      | Default                 | Required | Description                                          |
| ----------- | --------- | ----------------------- | -------- | ---------------------------------------------------- |
| chain-id    | string    | null                    | true     | chain id of the full node to connect                 |
| node        | URL       | "tcp://localhost:46657" | true     | address of the full node to connect                  |
| laddr       | URL       | "tcp://localhost:1317"  | true     | address to run the rest server on                    |
| trust-node  | bool      | "false"                 | true     | Whether this LCD is connected to a trusted full node |
| trust-store | DIRECTORY | "$HOME/.lcd"            | false    | directory for save checkpoints and validator sets    |

**Sample command** :

```
gaiacli light-client --chain-id=test --laddr=tcp://localhost:1317  --node tcp://localhost:46657 --trust-node=false
```

## LCD Use Cases

LCD could be very helpful for related service providers. For a wallet service provider, LCD could make transaction faster and more reliable in the following cases. 

1. Create An Account

![deposit](https://github.com/irisnet/cosmos-sdk/raw/bianjie/lcd_spec/docs/spec/lcd/pics/create-account.png)

First you need to get a new seed phrase :[get-seed](https://github.com/irisnet/cosmos-sdk/blob/bianjie/lcd_spec/docs/spec/lcd/api.md#keysseed---get)

After having new seed, you could generate a new account with it : [keys](https://github.com/irisnet/cosmos-sdk/blob/bianjie/lcd_spec/docs/spec/lcd/api.md#keys---post)

  

2. Transfer Asset

   ![transfer](https://github.com/irisnet/cosmos-sdk/raw/bianjie/lcd_spec/docs/spec/lcd/pics/transfer-tokens.png)


  The first step is to build an asset transfer transaction. Here we can post all necessary parameters to /create_transfer to get the unsigned transaction byte array. Refer to this link for detailed operation: [build transaction](https://github.com/irisnet/cosmos-sdk/blob/bianjie/lcd_spec/docs/spec/lcd/api.md#create_transfer---post)

  Then sign the returned transaction byte array with users' private key. Finally broadcast the signed transaction. Refer to this link for how to broadcast the signed transaction: [broadcast transaction](https://github.com/irisnet/cosmos-sdk/blob/bianjie/lcd_spec/docs/spec/lcd/api.md#create_transfer---post)