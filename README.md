<p align="center">
  <img width="100%" alt="FAN progress" src="docs/assets/progress-1.jpg">
</p>


OST.sol: the security token contract.

FAN-G: governance token contract. FAN-G is used as interest of repayment, and in other functions that manages the system.

FAN: stable coin, the name is FAN

Mortgage: the main contract that accepts assets, such as security tokens, and issues stable coins pegged by the price of the assets in USD.

Oracle: read the external data, such as real estate housing price, secondary market price

Emergency shutdown: End.sol shuts down the system in case emergency occurs. 


## Issuance period:

During this time, the stable coin issuer(the lender, admin) deploys the Morgage contract on the etherium blockchain. Following this, the borrower deposits their collateral(OST tokens ) using pledge(...). 

Pledge(...) examins the deposit amount of assets and issues the equal value in USD of FAN. Then transfer the LTV(Load To Value) amount of FANs to borrower's address and the discount to the Morgage contract address. The colleteral is locked in the Morgage contract till the borrower repays the sufficient FAN (the FAN borrowed plus interest in this period). 


## Loan Period 

Once the borrower has accepted the loan(FAN) amount, the Loan Period begins. Once the Loan Period is finished, the borrower is expected to repay the loan. If he does, he calls repayment(...) that can accept the repayment, unlocks the assets(OST) and then refunds the borrower's collateral amount. The repayed stable coins(FAN) are burned.

In the case that the borrower defaults or does not repay the full principal plus interest amount, the lender can choose to not accept the loan repayment, and the parties can opt for liquidation of the collateral in the Selling Period.


## Selling period:

In the case of a default, or the lender not accepting the borrower repayment, or when the asset's price plummits on the outside market and the value of assets is lower than the value of stable coins issued, the lender can opt for liquidation of the collateral through the process(sell(...)) selling out the collateral(OST). The selling period can only be initiated by the lender.

At the end of selling period, if the colleteral is not fully liquidated, the lender shall reduce(reduction(...)) the price, and list them for sale again. Any user can use buy(...) to buy the colleteral at a certain listed price, his FAN will be burned after he calls buy(...).

## How much is burned:

When borrower deposites 100 USD valued OST, the lender issues 100 FANs, transfers 80 FANs to the borrower and locks 20 FANs in the Morgage contract. In this case the loan to value is 80%. 

After borrower repays 80 FANs, the total 100 FANs will be burned. 

If on default, the lender opts to liquidate by selling out OST, he may only cut a deal on price 60,  because the OST's price plummits, then the lender can only burn 60+20 FANs. Their will be 20 FANs in lock.  

## Emergency Shutdown:

In the case of a system upgrade or unpredicatble emergencies, such as market irrationality, a hack, or a security breach, emergency shutdown is triggerd. 

Emergency Shutdown contract stops and shuts down the Morgage contract, ensuring that no more loans can be created, therefore no FAN will be issued afterwards. While borrower is still able to redeem their colleteral, and the lender can keep liquidating the colleteral.

The process of emergency shutdown is controlled by govenance token holders, who can trigger it by depositing FAN-G into the emergency shutdown contract, and call cage(...)  to execute. Once users deposit FAN-G into the ES, it is locked in the contract.

