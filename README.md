# 游戏场景
## 该游戏假设有5名玩家(player1 player2 player3 player4 player5),20名运动员(sam1-sam20),共同组建了5支虚拟球队(team1-team5).每名玩家投注成本为10个EOS。合约可以选择将多少数量的赌注按照分数高低奖励给前2名球队的创建者。
## 具体的执行过程
### 创建一名运动员
```
 cleos --wallet-url "http://127.0.0.1:8888" push action eosio newfber ./fber.json -p eosio

 cat fber.json
[
{
 "name": "sam1",
"country": China,
"jersey_number":3,
"price": "100.0000 EOS"
"score": 0
}
]
```
#### 获取所有球员信息列表
```
cleos get table eosio footballer
```
### 组建一支虚拟球队

```
cleos --wallet-url "http://127.0.0.1:8888" push action eosio newteam ./team.json -p user1
cat team.json
[
{
"owner": "user1",
"banker": "eosio.token"
"players":[0,2],
"scoresum": 0,
"cost": "10.0000 SYS",
"stake": "50.0000 SYS",
"gameid": 2
}
]

```
#### 获取所有球队信息列表
```
cleos get table eosio team
```
### 更新一名球员的分数
```
cleos --wallet-url  "http://127.0.0.1:8888" push action eosio updatescore '[{"id":0,"score":4}]' -p eosio

```

### 更新所有虚拟球队的总分数

```
cleos --wallet-url "http://127.0.0.1:8888" push action eosio teamscore '[1]' -p eosio

```
### 所有虚拟球队总成绩排序

```
cleos --wallet-url "http://127.0.0.1:8888" push action eosio teamsort '[1]' -p eosio
```


### 获取所有虚拟球队的目前排名
```
cleos get table eosio eosio result
```

### 发放奖励
```
cleos --wallet-url "http://127.0.0.1:8888" push action eosio reward ./reward.json -p eosio

cat reward.json
{
"gameid":1,
"bonus": "1.9000 SYS",
"number": 5

}
```
