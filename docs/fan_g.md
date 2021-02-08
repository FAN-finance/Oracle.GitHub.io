# FAN治理币

<a href="https://github.com/omnilaboratory/OmniBOLT-spec/blob/master/LICENSE" target="_blank" rel="noopener"><img src="https://img.shields.io/badge/license-MIT-brightgreen" data-origin="https://img.shields.io/badge/license-MIT-brightgreen" alt=""></a> <a href="#/"><img src="https://img.shields.io/badge/made%20by-Fan%20Foundation-blue" data-origin="https://img.shields.io/badge/made%20by-Fan%20Foundation-blue" alt=""></a> <a href="https://github.com/omnilaboratory/obd" target="_blank" rel="noopener"><img src="https://img.shields.io/badge/project-fan%20g-orange" data-origin="https://img.shields.io/badge/project-fan%20g-orange" alt=""></a>

在FAN的生态系统中，治理币充当着十分重要的角色。既是社区治理的权利象征，又是激励整个社区良性循环的有效手段。

**治理币基本参数**

| 参数     | 值                  |
| -------- | ------------------- |
| 名称     | FAN Governance Coin |
| 符号     | FGC 或 fanG         |
| 小数位   | 18                  |
| 发行总量 | 不定量              |

**关联项目**

- 社区投票
- 抵押贷款
- 预言机
- 交易所

## 1. 应用场景

#### 1.1 社区投票

治理币首要功能即作为治理社区的权利象征。

社区用户通过抵押冻结治理币的方式获取投票权。每一个被抵押的治理币相当于一枚选票。

当社区需要作出重大决策时，社区所有用户均可通过投票系统进行决策，投票的结果将会直接影响各项目的运营策略。

投票时，代理币将会被锁定在具体投票的项目中，待投票结束时自动解锁。

只要治理币没有因投票被冻结，社区用户有权利随时将抵押在投票合约中的未锁定的治理币提取回自己的钱包账户。

#### 1.2 抵押抵款

治理币在抵押贷款合约中可以有2种使用方法：

- 随抵押行为发放（即挖矿奖励）
- 作为还款利息，支付给抵押合约

#### 1.3 预言机

治理币在预言机系统中，连接了**数据消费者**和**数据提供者**这两大角色。

数据消费者请求数据时，将治理币作为报酬支付给预言机合约。

预言机合约在完成筛选**数据提供者**提供的数据后，按照既定的**分配规则**将受到的报酬分发给数据提供者节点。

#### 1.4 交易所

治理币可以支持交易所的奖励机制。

- 创建交易对奖励
- 交易奖励

## 2. 发行及销毁规则

#### 2.1 发行规则

首次发行治理币40万个，由开发团队保留，用于初期运营。

其他治理币均随**挖矿行为**铸币生成。

**挖矿行为奖励表**

| 模块     | 行为             | 奖励点数 |
| -------- | ---------------- | -------- |
| 抵押贷款 | 抵押资产         | 100      |
|          | 按时还款         | 50       |
|          | 购买清算中的资产 | 50       |
| 交易所   | 创建交易池       | 100      |
|          | 增加流动性       | 50       |



#### 2.2 销毁规则



## 3. 技术需求

- 符合ERC-20标准
- 符合ERC-667标准，拥有transferAndCall方法
- 具备mint和burn功能
- 具备auth授权功能，允许通过授权的合约调用mint功能增发新币
- 具备ApproveAndCall方法