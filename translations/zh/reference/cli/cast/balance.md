# cast balance

以 Wei 为单位获取账户余额

```bash
$ cast balance --help
Usage: cast balance [OPTIONS] <WHO>

Arguments:
  <WHO>
          The account to query

Options:
  -B, --block <BLOCK>
          The block height to query at.
          
          Can also be the tags earliest, finalized, safe, latest, or pending.

  -e, --ether
          Format the balance in ether

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
```