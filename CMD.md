# 游戏场景
#### 该游戏假设有5名玩家(*player1*...*player5*),20名运动员(*sam1*...*sam20*),共同组建了5支虚拟球队(*team1*...*team5*).每名玩家投注成本为10个**ESM**。合约根据奖励规则选择将一定数量的奖金按照每只球队分数高低奖励给前**X**名球队的创建者。

#####  查看可选的运动员
```
 cleos --wallet-url "http://127.0.0.1:8888" get table bet4worldcup bet4worldcup players

```
#####  查看目前的竞赛房间
```
 cleos --wallet-url "http://127.0.0.1:8888" get table bet4worldcup bet4worldcup rooms

```
#####  查看近期的比赛日程
```
 cleos --wallet-url "http://127.0.0.1:8888" get table bet4worldcup bet4worldcup schedule

```
##### 组建一支虚拟球队

```
cleos --wallet-url "http://127.0.0.1:8888" push action bet4worldcup regteam '{"item":["player1",0,0,1530194400,"1000 ESM","10 ESM","1,2,4,5,10,11"]}' -p player1

```
##### 获取所有球队信息列表
```
 cleos --wallet-url "http://127.0.0.1:8888" get table bet4worldcup bet4worldcup teams
```
##### 更新一名球员的分数
```
cleos --wallet-url  "http://127.0.0.1:8888" push action bet4worldcup updateperf '{"item":[2,1530194400,98,"assistant","stats.com"]}' -p esmadmin1111

```

##### 计算球队总分数

```
cleos --wallet-url "http://127.0.0.1:8888" push action bet4worldcup calscore '{"id":1}'

```
##### 一个竞赛房间的所有虚拟球队总成绩排序

```
cleos --wallet-url "http://127.0.0.1:8888" push action bet4worldcup teamsort '{"room_id":0}' -p esmadmin1111
```

##### 计算一个竞赛房间的总投注量

```
cleos --wallet-url "http://127.0.0.1:8888" push action bet4worldcup stakesum '{"room_id":0}' -p esmadmin1111
```
##### 获取所有虚拟球队的目前排名
```
cleos get table eosio eosio result
```

##### 领取自己的奖励
```
cleos --wallet-url "http://127.0.0.1:8888" push action bet4worldcup claimrewards '{"room_id":0,"team_id":0}' -p esmadmin1111 -p eossmcbanker

```

参数详情可查看sportsminer.abi文件
