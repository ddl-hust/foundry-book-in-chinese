# cast receipt

Get the transaction receipt for a transaction

```bash
$ cast receipt --help
Usage: cast receipt [OPTIONS] <TX_HASH> [FIELD]

Arguments:
  <TX_HASH>
          The transaction hash

  [FIELD]
          If specified, only get the given field of the transaction

Options:
      --confirmations <CONFIRMATIONS>
          The number of confirmations until the receipt is fetched
          
          [default: 1]

      --async
          Exit immediately if the transaction was not found
          
          [env: CAST_ASYNC=]

  -r, --rpc-url <URL>
          The RPC endpoint
          
          [env: ETH_RPC_URL=]

      --flashbots
          Use the Flashbots RPC URL (https://rpc.flashbots.net)

      --jwt-secret <JWT_SECRET>
          JWT Secret for the RPC endpoint.
          
          The JWT secret will be used to create a JWT for a RPC. For example, the following can be used to simulate a CL `engine_forkchoiceUpdated` call:
          
          cast rpc --jwt-secret <JWT_SECRET> engine_forkchoiceUpdatedV2 '["0x6bb38c26db65749ab6e472080a3d20a2f35776494e72016d1e339593f21c59bc",
          "0x6bb38c26db65749ab6e472080a3d20a2f35776494e72016d1e339593f21c59bc", "0x6bb38c26db65749ab6e472080a3d20a2f35776494e72016d1e339593f21c59bc"]'
          
          [env: ETH_RPC_JWT_SECRET=]

  -h, --help
          Print help (see a summary with '-h')

Display options:
  -j, --json
          Print as JSON
```