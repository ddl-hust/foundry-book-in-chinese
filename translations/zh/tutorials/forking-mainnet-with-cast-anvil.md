## 使用 Cast 和 Anvil 分叉主网

### 介绍

通过结合 [Anvil][anvil] 和 [Cast][cast]，您可以通过与真实网络上的合约交互来进行分叉和测试。 本教程的目的是向您展示如何将 Dai 代币从持有 Dai 的人转移到 Anvil 创建的帐户。

### 设置

让我们从分叉主网开始。

```sh
anvil --fork-url https://mainnet.infura.io/v3/$INFURA_KEY
```

您将看到使用公钥和私钥创建了 10 个帐户。 我们将使用 `0xf39fd6e51aad88f6f4ce6ab8827279cfffb92266`（我们称此用户为 Alice）。

### 转账 Dai

转到 Etherscan 并搜索 Dai 代币的持有者（[此处](https://etherscan.io/token/0x6b175474e89094c44da98b954eedeac495271d0f#balances)）。 让我们选择一个随机帐户。 在此示例中，我们将使用`0xad0135af20fa82e106607257143d0060a7eb5cbf`。 让我们将合约和帐户导出为环境变量：

```sh
export ALICE=0xf39fd6e51aad88f6f4ce6ab8827279cfffb92266
export DAI=0x6b175474e89094c44da98b954eedeac495271d0f
export LUCKY_USER=0xad0135af20fa82e106607257143d0060a7eb5cbf
```

我们可以使用 [`cast call`][cast-call] 检查 Alice 的余额：

```sh
$ cast call $DAI \
  "balanceOf(address)(uint256)" \
  $ALICE
0
```

同样，我们也可以使用 `cast call` 查看幸运用户的余额：

```sh
$ cast call $DAI \
  "balanceOf(address)(uint256)" \
  $LUCKY_USER
71686045944718512103110072
```

让我们使用 [`cast send`][cast-send] 将一些代币从幸运用户转移给 Alice：

```sh
# This calls Anvil and lets us impersonate our lucky user
$ cast rpc anvil_impersonateAccount $LUCKY_USER
$ cast send $DAI \
--unlocked \
--from $LUCKY_USER \
  "transfer(address,uint256)(bool)" \
  $ALICE \
  1686045944718512103110072
blockHash               0xbf31c45f6935a0714bb4f709b5e3850ab0cc2f8bffe895fefb653d154e0aa062
blockNumber             15052891
...
```

让我们检查交易是否有效：

```sh
cast call $DAI \
  "balanceOf(address)(uint256)" \
  $ALICE
1686045944718512103110072

$ cast call $DAI \
  "balanceOf(address)(uint256)" \
  $LUCKY_USER
70000000000000000000000000
```

[anvil]: ../reference/anvil/README.md
[cast]: ../reference/cast/README.md
[cast-call]: ../reference/cast/cast-call.md
[cast-send]: ../reference/cast/cast-send.md
