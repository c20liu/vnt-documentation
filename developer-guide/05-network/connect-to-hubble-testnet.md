# 如何加入VNT Hubble测试网

本文目录：
- [测试网基本信息](#测试网基本信息)
- [加入测试网](#加入测试网)
- [测试网水龙头](#测试网水龙头)
- [其他资料](#其他资料)


## 测试网基本信息

VNT Hubble测试网共部署了19个见证人节点，负责执行交易和打包区块，部署了3个公共全节点，并开启了RPC服务，查询和发送交易时可以使用这些公共全节点。

19个初始的见证人P2P地址：

```bash
"/ip4/192.168.9.47/tcp/3002/ipfs/1kHM6j2xYV3588TQUBMkczjH3Lk21t8YzsfCguV4LNGyXwf",
"/ip4/192.168.9.37/tcp/3002/ipfs/1kHC7NbWu7BcbcofTZk6NDS8Gtj65f9nouonGfdoFZS1ojm",
"/ip4/192.168.9.55/tcp/3002/ipfs/1kHXTyAYi4dvFbmGQg57mUUGPMwUJ3yUeri5uFERuRVXNys",
"/ip4/192.168.9.46/tcp/3002/ipfs/1kHRaq2mbwQkyQ1WXkyxijnDCcEeNQqHxDCYcdMgKwrXppD",
"/ip4/192.168.9.29/tcp/3002/ipfs/1kHQwe3GNFLMBsM4L77gEffqRR9GW7wzMsEqL6SuaCqrono",
"/ip4/192.168.9.36/tcp/3002/ipfs/1kHdWmmCNQDj77yjz5mrwRd69tSete7BtJmXc4qycutz9G4",
"/ip4/192.168.9.30/tcp/3002/ipfs/1kHVoW4sbWcaXuHwfSF66EeMZei1zEKY7zXw8UoR8Zgv9bm",
"/ip4/192.168.9.51/tcp/3002/ipfs/1kHH454XPAGwQCLrsMUSssunnuzPVF8Xeq2Pgt4wBk7iKGu",
"/ip4/192.168.9.26/tcp/3002/ipfs/1kHJFnmxboK28cmvkWPPaDNv2PBAkPPc7THRcWTWePA9uMy",
"/ip4/192.168.9.54/tcp/3002/ipfs/1kHTbtbVpdpzBJPBuXyp9RG3Paf1Xmmvc6qC1dDohwsxDaV",
"/ip4/192.168.9.24/tcp/3002/ipfs/1kHNzJtaKuMbaQvMQDVSRqFck9ZrsfbLN56DcgxVRb1WaF9",
"/ip4/192.168.9.107/tcp/3002/ipfs/1kHSMSf2RzmRhCjEXHp1ZzYhivRcgo2ST7jQPxpY1ZfaxGi",
"/ip4/192.168.9.79/tcp/3002/ipfs/1kHjWshrfFCfB1MW5p75oBuCJL2B4Sr8sedtaBbQuziNMa5",
"/ip4/192.168.9.3/tcp/3002/ipfs/1kHLsGfXFpjXvFcBqRHShiMmZ5b8PFe5QLfFujM7aCRaJcc",
"/ip4/192.168.9.112/tcp/3002/ipfs/1kHaqVK8jmvbqkzBhk3tYwWCsZk8eYfDXYpLJrygZ1z88iZ",
"/ip4/192.168.9.93/tcp/3002/ipfs/1kHMQwBzJEUUbRaub4keyeYtP3mx4ARYLDyqRwxGTWqpCZY",
"/ip4/192.168.9.66/tcp/3002/ipfs/1kHEpoAyuKU7Vs5QwaAYa7NUwePbE8cxDDceCHAymdUfAAV",
"/ip4/192.168.9.59/tcp/3002/ipfs/1kHH2gGtWhFvX7EM47imo3QTvMsu1368N1dEzdtBiQaJ9j5",
"/ip4/192.168.9.21/tcp/3002/ipfs/1kHhR4HmLhRSSw6tJey7awxYkCskDGTuHRYUVL2eUzAV1oL"
```

一个公共引导节点的P2P地址：
```bash
"/ip4/101.37.164.86/tcp/3002/ipfs/1kHbfUFUGYv6EPLYwYWdcS9d3HSoxHNqufDruj2aWcBTVKe"
```

3个公共全节点的RPC信息是：

```bash
http://101.37.164.86:8880
http://47.104.173.117:8880
http://47.111.100.232:8880
```

## 加入测试网

除了使用公共节点外，对于开发者还有更好的选择是，部署私有的全节点，该全节点可以部署在局域网内网和公网环境，但RPC信息不对外透露，实现了独自使用的目的。

第一步：部署节点首先要克隆`go-vnt`源码，具体安装和编译请关注go-vnt项目[README.md](<https://github.com/vntchain/go-vnt#%E4%BB%8E%E6%BA%90%E7%A0%81%E5%AE%89%E8%A3%85gvnt>)。

第二步：创建并进入节点目录。

```bash
cd ~
mkdir vntnode
cd vntnode
```

第三步：使用`init.json`文件初始化节点，测试网`init.json`内容如下：

```json
{
    "config": {
        "chainId": 2,
        "dpos": {
            "period": 2,
            "witnessesnum": 19,
            "witnessesUrl": [
                "/ip4/192.168.9.47/tcp/3002/ipfs/1kHM6j2xYV3588TQUBMkczjH3Lk21t8YzsfCguV4LNGyXwf",
                "/ip4/192.168.9.37/tcp/3002/ipfs/1kHC7NbWu7BcbcofTZk6NDS8Gtj65f9nouonGfdoFZS1ojm",
                "/ip4/192.168.9.55/tcp/3002/ipfs/1kHXTyAYi4dvFbmGQg57mUUGPMwUJ3yUeri5uFERuRVXNys",
                "/ip4/192.168.9.46/tcp/3002/ipfs/1kHRaq2mbwQkyQ1WXkyxijnDCcEeNQqHxDCYcdMgKwrXppD",
                "/ip4/192.168.9.29/tcp/3002/ipfs/1kHQwe3GNFLMBsM4L77gEffqRR9GW7wzMsEqL6SuaCqrono",

                "/ip4/192.168.9.36/tcp/3002/ipfs/1kHdWmmCNQDj77yjz5mrwRd69tSete7BtJmXc4qycutz9G4",
                "/ip4/192.168.9.30/tcp/3002/ipfs/1kHVoW4sbWcaXuHwfSF66EeMZei1zEKY7zXw8UoR8Zgv9bm",
                "/ip4/192.168.9.51/tcp/3002/ipfs/1kHH454XPAGwQCLrsMUSssunnuzPVF8Xeq2Pgt4wBk7iKGu",
                "/ip4/192.168.9.26/tcp/3002/ipfs/1kHJFnmxboK28cmvkWPPaDNv2PBAkPPc7THRcWTWePA9uMy",
                "/ip4/192.168.9.54/tcp/3002/ipfs/1kHTbtbVpdpzBJPBuXyp9RG3Paf1Xmmvc6qC1dDohwsxDaV",

                "/ip4/192.168.9.24/tcp/3002/ipfs/1kHNzJtaKuMbaQvMQDVSRqFck9ZrsfbLN56DcgxVRb1WaF9",
                "/ip4/192.168.9.107/tcp/3002/ipfs/1kHSMSf2RzmRhCjEXHp1ZzYhivRcgo2ST7jQPxpY1ZfaxGi",
                "/ip4/192.168.9.79/tcp/3002/ipfs/1kHjWshrfFCfB1MW5p75oBuCJL2B4Sr8sedtaBbQuziNMa5",
                "/ip4/192.168.9.3/tcp/3002/ipfs/1kHLsGfXFpjXvFcBqRHShiMmZ5b8PFe5QLfFujM7aCRaJcc",
                "/ip4/192.168.9.112/tcp/3002/ipfs/1kHaqVK8jmvbqkzBhk3tYwWCsZk8eYfDXYpLJrygZ1z88iZ",

                "/ip4/192.168.9.93/tcp/3002/ipfs/1kHMQwBzJEUUbRaub4keyeYtP3mx4ARYLDyqRwxGTWqpCZY",
                "/ip4/192.168.9.66/tcp/3002/ipfs/1kHEpoAyuKU7Vs5QwaAYa7NUwePbE8cxDDceCHAymdUfAAV",
                "/ip4/192.168.9.59/tcp/3002/ipfs/1kHH2gGtWhFvX7EM47imo3QTvMsu1368N1dEzdtBiQaJ9j5",
                "/ip4/192.168.9.21/tcp/3002/ipfs/1kHhR4HmLhRSSw6tJey7awxYkCskDGTuHRYUVL2eUzAV1oL"
            ]
        }
    },
    "timestamp": "0x5b45b949",
    "extraData": "0x",
    "gasLimit": "0x47b760",
    "difficulty": "0x1",
    "coinbase": "0x0000000000000000000000000000000000000000",
    "alloc": {
        "0x02f8d9c9bb81b3a81bf13d4ec8818be5918d3658": {
            "balance": "0x9b18ab5df7180b6b8000000"
        },
        "0xa0959738e3555c54577cca3c721b674c5c18072e": {
            "balance": "0x6765c793fa10079d0000000"
        },
        "0xf3e3b67550a6f37f596a1ba2e7357e946c82c905": {
            "balance": "0x6765c793fa10079d0000000"
        },
        "0x838c5c23372ccd88fc5fc4943e2eda5f3a0ec35e": {
            "balance": "0x6765c793fa10079d0000000"
        }
    },
    "witnesses": [
        "0x739c36e1a03fef990c7adea519a1f71562b62c00",
        "0x38697dfa982236ad122fb839fb500a77ef74485f",
        "0x896c06ab6edb205ecfd3b6e8922e0160c21a639f",
        "0x41a440e8373f2f6ce1cdb65d715c4282a9f7072c",

        "0x36ad51a93be1bfb24f1d83ce743d452b9614653b",
        "0x51ce27acac3ff0163e5eb90bd8054ac022522ed4",
        "0x7f42760749d5795617e13d8274b00ff3d9236a0e",
        "0x9599d9527f1b873726ec401c4105af19519af0ba",
        "0xff29e84aae64d262fa5aa59d09042e6ed0fb015f",

        "0x31418db5ec778c6148fb61ad2db0bd6e6cfd2235",
        "0x950802b12e1c6b9fec4ce8bdadef2bae6c85b82e",
        "0x9af0b2598e6990886ed6baabd662f88f67eacc68",
        "0x6928360b84d73addf9e9f99856f50891da4baea1",
        "0xa2aa9dc8c203158be660dd664f9aff8d5253e0b4",

        "0x480ed56bee33a27d5580b0c221fbb15437f8abd5",
        "0xc10988084211f2aa23fe2c2035c8aba3226a3bd0",
        "0x8535fa644a28d2867c27f429c2e1d719b20f50b2",
        "0xceb13af43dcc22dd62726f838e98a3c403c8dc08",
        "0x4fbf6ebc18656ba6955e44f89b6eeef72eec21eb"
    ],
    "number": "0x0",
    "gasUsed": "0x0",
    "parentHash": "0x0000000000000000000000000000000000000000000000000000000000000000"
}
```

创建`init.json`文件，并写入以上内容。然后使用`init.json`进行初始化：

```bash
gvnt init init.json --datadir .
```

第四步：创建gvnt账号，可以设置密码：

```bash
gvnt account new .
```

如果你已经有账号，可以直接将账号keystore文件拷贝到`vntnode/keystore`目录。

第五步：使用公共全节点的p2p地址作为bootnode，启动私有节点：

```bash
gvnt --networkid 2 --datadir . --port 3001 --vntbootnode "/ip4/101.37.164.86/tcp/3002/ipfs/1kHbfUFUGYv6EPLYwYWdcS9d3HSoxHNqufDruj2aWcBTVKe" --syncmode full --rpc --rpcaddr 0.0.0.0 --rpcport 8880 --rpcapi="db,core,net,vnt,personal" console
```



成功执行以上5步，你应当已经连接上了VNT Hubble测试网，并且开始同步区块，区块同步可采用以下方法查看：

通过`attach`命令连接到节点：
```bash
$ cd vntnode
$ gvnt attach gvnt.ipc
```

查看同步：
```bash
> core.syncing
{
  currentBlock: 1992176,
  highestBlock: 2003529,
  knownStates: 0,
  pulledStates: 0,
  startingBlock: 1990059
}
```

## 测试网水龙头

在测试网上进行开发和测试，需要使用VNT测试代币，如果你的账号没有代币，或代币不足，可在[测试网水龙头](https://hubscan.vnt.link/faucet)申请测试代币。

## 其他资料

1. 如果你想成为Hubble超级节点，请查看[如何成为超级节点](https://github.com/vntchain/vnt-documentation/blob/master/developer-guide/04-bp/become-to-witness.md)。
2. 如果你想加入Hubble主网，成为全节点，请查看[如何加入Hubble主网](https://github.com/vntchain/vnt-documentation/blob/master/developer-guide/05-network/connect-to-hubble-network.md)。
