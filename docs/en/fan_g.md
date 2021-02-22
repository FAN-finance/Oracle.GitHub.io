# FAN Governance Token

<a href="https://github.com/omnilaboratory/OmniBOLT-spec/blob/master/LICENSE" target="_blank" rel="noopener"><img src="https://img.shields.io/badge/license-MIT-brightgreen" data-origin="https://img.shields.io/badge/license-MIT-brightgreen" alt=""></a> <a href="#/"><img src="https://img.shields.io/badge/made%20by-Fan%20Foundation-blue" data-origin="https://img.shields.io/badge/made%20by-Fan%20Foundation-blue" alt=""></a> <a href="https://github.com/omnilaboratory/obd" target="_blank" rel="noopener"><img src="https://img.shields.io/badge/project-fan%20g-orange" data-origin="https://img.shields.io/badge/project-fan%20g-orange" alt=""></a>

In the FAN ecosystem, governance tokens play a very important role. It is not only a right symbol of community governance, but also an effective means to inspire a virtuous circle of the entire community.

**basic parameters of governance token**

|Parameters| Value                 |
| -------- | -------------------   |
| Name     | FAN Governance Token  |
| ID       | FGC 或 fanG           |
| Decimals | 18                  |
| Issuance Amount | unsettled      |

**Related Otems**

- Community Vote
- Mortgage
- Oracle
- Exchange

## 1. Applicable Situations

#### 1.1 Community Vote

The primary function of governance token is to serve as the right symbol of governance community.

Community users obtain voting rights by mortgage freezing governance tokens. Each pledged governance token is equivalent to one vote.

When the community needs to make a major decision, all users in the community can make a decision through the voting system, and the result of the vote will directly affect the operation strategy of each project.

When voting, the governance token will be locked in the specific voting project and will be automatically unlocked when the voting ends.

As long as the governance token is not frozen due to voting, community users have the right to withdraw the unlocked governance currency pledged in the voting contract back to their wallet account at any time.

#### 1.2 Mortgage

The governance tokens can be used in two ways in a mortgage loan contract:

- issued with mortgage behavior (ie mining rewards)
- as repayment interest, paid to the mortgage contract

#### 1.3 Oracle

In the oracle system, the governance token connects the two major roles of **data consumer** and **data provider**.


When a data observer requests data, the governance currency is paid as a reward to the oracle contract。

After the oracle contract completes the screening of the data provided by the **data provider**, it distributes the rewards received to the data provider nodes in accordance with the established **distribution rules**.

#### 1.4 交易所

Governance tokens can support the exchange's reward mechanism.

- create trading pair(s) reward
- transaction reward

## 2. Issuance and Destruction Rules

#### 2.1 Issuance Rules

400,000 governance tokens are issued for the first time, which will be reserved by the development team for initial operation.

Other governance tokens are generated with the minting of **mining behavior**.

**Mining Behavior Reward Table**

| Modules  | actions             | awards   |
| -------- | ----------------    | -------- |
| Mortgage | mortgage            | 100      |
|          | pay in-time         | 50       |
|          | buy collaterals.    | 50       |
| exchange | build pool          | 100      |
|          | add liquidity       | 50       |



#### 2.2 Destruction Rules


## 3. Tech Demands

- comply with ERC-20 standard
- comply with ERC-667 standard and have transferAndCall method
- have mint and burn function
- have the auth authorization function, allowing the mint function to be called through authorized contracts to issue new tokens
- have ApproveAndCall method