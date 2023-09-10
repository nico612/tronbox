
官方文档：https://developers.tron.network/reference/tronbox-quickstart

## tronbox 安装

`npm install -g tronbox`

## 编译

`tronbox compile` OR `yarn compile`


## 部署

部署到本运行环境 TronBox Runtime Environment (TRE)

docker 下载 image

`docker pull tronbox/tre`

运行

`docker run -it -p 9090:9090 --rm --name tron tronbox/tre` OR  `yarn run`

文档image说没有对 Apple ARM 芯片做优化，可能需要多重新运行几次，但是我一次就启动好了

``` shell
docker run -it -p 9090:9090 --rm --name tron tronbox/tre

----------------------------------

TronBox Runtime Environment v1.0.3

----------------------------------

Start the http proxy for dApps...
[HPM] Proxy created: /  ->  http://127.0.0.1:18190
[HPM] Proxy created: /  ->  http://127.0.0.1:18191
[HPM] Proxy created: /  ->  http://127.0.0.1:8545
[HPM] Proxy created: /  ->  http://127.0.0.1:8545
[HPM] Proxy created: /  ->  http://127.0.0.1:8060

 TRE now listening on http://127.0.0.1:9090


ADMIN /admin/accounts-generation

FullNode is already.

...
Loading the accounts and waiting for the node to mine the transactions...
(1) Waiting for receipts...
Sending 10000 TRX to TBhSLhCQoCZ1QPx5BhJkA9XxM8hdobxqcE
Sending 10000 TRX to TUu9cLetGn3QjuDRuHDbMnyEmzWiRs291p
Sending 10000 TRX to TV57Bw157LAMy2tdp2N7qtEjZShWTdFY2o
Sending 10000 TRX to TMhy4XfpfnfhAU3zfcfiRhTNRBFZ8heAGM
Sending 10000 TRX to TUwxGDPwv8fTBdF5R9uvmqhr4kMCXzyGQg
Sending 10000 TRX to TCrJPfpkHEF8rMQmPVEwPEfXfcjU4ThU7y
Sending 10000 TRX to TEbgxKbzQ44SYHcHWKcuBuYsse4W5LyAYZ
Sending 10000 TRX to TDX7uerSZbBZS7HMg6CEV6HzsaZKA7c1j9
Sending 10000 TRX to TKz9ZkSx8NrwqNdaHgBx7dKSg96B1TWiyW
Sending 10000 TRX to TJsgfMEhzSHePfJtqXC2CFT4J7QBM5Az5s
Sleeping for 3 seconds... Slept.
(2) Waiting for receipts...
Sleeping for 3 seconds... Slept.
(3) Waiting for receipts...
Done.

Available Accounts
==================

(0) TBhSLhCQoCZ1QPx5BhJkA9XxM8hdobxqcE (10000 TRX)
(1) TUu9cLetGn3QjuDRuHDbMnyEmzWiRs291p (10000 TRX)
(2) TV57Bw157LAMy2tdp2N7qtEjZShWTdFY2o (10000 TRX)
(3) TMhy4XfpfnfhAU3zfcfiRhTNRBFZ8heAGM (10000 TRX)
(4) TUwxGDPwv8fTBdF5R9uvmqhr4kMCXzyGQg (10000 TRX)
(5) TCrJPfpkHEF8rMQmPVEwPEfXfcjU4ThU7y (10000 TRX)
(6) TEbgxKbzQ44SYHcHWKcuBuYsse4W5LyAYZ (10000 TRX)
(7) TDX7uerSZbBZS7HMg6CEV6HzsaZKA7c1j9 (10000 TRX)
(8) TKz9ZkSx8NrwqNdaHgBx7dKSg96B1TWiyW (10000 TRX)
(9) TJsgfMEhzSHePfJtqXC2CFT4J7QBM5Az5s (10000 TRX)

Private Keys
==================

(0) ef63e02377073006690fa2711fa95c3c758ea98f633cde59c474610150979ac7
(1) 40cfa6893340378dd3be4bcc9e2620f456ace1a115874a239f073fc2598db513
(2) d2fbee0fcf599bb41bff7fc315d6504e2026d7972181792b4435a60fcd7cef91
(3) 38b59a6d3d83f1b519c3749cf3e8be6f142a91992564660bdb183120a553b4be
(4) 023cafd7ae992741b5ac19f7447cbf047edae33953af5978d1b9f7b72873ae6e
(5) e6310c1f835096a2d5f4fa0cdd3d0afc6a9389fa6175b7d28c2afaa63cbb8a88
(6) 5f0fabef0af46d1bdad82d6b6b3ee29474251b5ef18328de2d29089865623c09
(7) 5b3791db5d83deeb68ec3aaefe576182f1828505837afa31efb5658ccfde0250
(8) 1e99b05ede88e0540cf807cdf0b7b3f47bdbe4e92735a12b858d4853f40bb351
(9) 4a017cabe30dbc2bab191da33143317c9940e3319a85fb3f356c8e33289c042e

HD Wallet
==================
Mnemonic:      garlic lab left cement bring tenant sad response they guess equip pumpkin
Base HD Path:  m/44'/195'/0'/0/{account_index}

GET 200  - 6501.353 ms
```



## 测试

`tronbox test ./test/metacoin.js` OR `tronbox test ./test/metacoin.js`


## 合约交互

启动控制台
```shell
tronbox console
# 然后输出，development 为当前连接的网络
tronbox(development)>
```

查询余额
```shell
tronbox(development)> tronWeb.trx.getAccount()
```

查询账户

```shell
tronbox(development)> tronWeb._accounts
```

调用合约查询余额
```shell
tronbox(development)> MetaCoin.deployed().then(res => res.getBalance(tronWeb._accounts[0]))
```

合于转账

``` shell
tronbox(development)> MetaCoin.deployed().then(res => res.sendCoin(tronWeb._accounts[1],500))

```

查询接收账户余额

```shell
tronbox(development)> MetaCoin.deployed().then(res => res.getBalance(tronWeb._accounts[1]))

```

更多介绍：
https://developers.tron.network/reference/install