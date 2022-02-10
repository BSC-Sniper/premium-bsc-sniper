### BSC Sniper

BSC Sniper is a tool that helps you to buy BSC project's tokens in Pancakeswap or ApeSwap listing/launches, for both BNB and BUSD pairs.. Easy to use, and it run locally in your machine. You don't need to send me anything, maybe a little donation if this works for you. :D

<H2>Prerequisites</H2>

 - Your BSC (Binance Smart Chain) Wallet Address 
 - Windows x64 machine
 - Internet, obviously to conenct to BSC network, send and sign transactions.

<H2>Getting started</H2>

1. Clone (Download) this repository <a href="https://github.com/BSC-Sniper/premium-bsc-sniper">here</a>.
2. You will download a .zip, extract it in your Desktop or any folder you want.
3. You will find a folder called _"premium-bsc-sniper"_ and into it a few files (**DO NOT DELETE ANY FILES OR MODIFY ANYTHING**). These files:
    - **config.json** ; the most important one. This file contain your information
    - **abi.json** ; this is the contracts ABI. You won't need to change anything in this file, if not needed.
    - **bscsniper.exe** ; the executable, the magic.
4. Copy the path of your folder where you extracted the .zip (ie: C:\Users\user\premium-bsc-sniper\bscsniper) and open your terminal (_Windows Search > cmd_) and go to the folder you extract all these files using the `cd` command (change directory) > example: `cd C:\Users\user\premium-bsc-sniper\bscsniper`
5. Execute the `bscsniper.exe --help` and you'll find your options.

<H2>Configuration File (config.json)</H2>

Open **_config.json_** file with a text editor and you will find these parameters:

```
{
  "pancakeFactory":"0xcA143Ce32Fe78f1f7019d7d551a6402fC5350c73",
  "pancakeRouter":"0x10ED43C718714eb63d5aA57B78B54704E256024E",
  "yourWallet":"YOUR_WALLET_HERE",
  "yourPrivateKey":"YOUR_PRIVATE_HERE",
  "BNB":"0xbb4CdB9CBd36B01bD1cBaEBF2De08d9173bc095c",
  "BUSD":"0xe9e7cea3dedca5984780bafc599bd69add087d56"
}
```

Be sure to change `YOUR_WALLET_HERE` and `YOUR_PRIVATE_HERE` for your information.

- **pancakeFactory**: This is the Pancake Factory Contract. With this token is how the project create their Liquidity Pools (LP). Is used to validate if token has been created the LP contract. You can find this information directly in PancakeSwap (PancakeSwap Factory V2): https://docs.pancakeswap.finance/code/smart-contracts. You don't need to change anything here if you want to buy in PancakeSwap.
- **pancakeRouter**: This is the contract that is used to buy/sell token in PancakeSwap. For example, when you swap token in PancakeSwap's website, this is the contract they used to swap. You can find this information directly in PancakeSwap (PancakeSwap Router V2): https://docs.pancakeswap.finance/code/smart-contracts. You don't need to change anything here if you want to buy in PancakeSwap.
- **yourWallet**: Your Metamask address. The address you will use to buy/sell tokens. Obviously you need BNB to pay fees.
- **yourPrivateKey**: This is your Metamask Private Key and it's used to sign your transactions. If you don't configure this private, you won't be able to buy/sell/appove any token. If you don't know how to find it, check this out: https://metamask.zendesk.com/hc/en-us/articles/360015289632-How-to-Export-an-Account-Private-Key. **THIS IS NOT YOUR SEED. DO NOT SHARE YOUR SEED PHRASE WITH ANYONE. DO NOT SHARE ANY OF THIS INFORMATION WITH ANYONE.**
- **BNB**: WBNB token. It's used if you want to buy/sell/appove with this pair. You don't need to change anything here. You can check it here: https://coinmarketcap.com/currencies/wbnb/
- **BUSD**: BUSD token. It's used if you want to buy/sell/appove with this pair. You don't need to change anything here. You can check it here: https://coinmarketcap.com/currencies/busd/

**IMPORTANT**: Yes, I know the "yourPrivateKey" param scares you (it scared me too at first), but you need it to buy (sign transactions) faster than anyone. I recommend you to use a new wallet just for the sniper. **Do not use your main wallet, for your peace of mind.**

If the token that you want to buy in listing is in ApeSwap, you'll need to change "pancakeFactory" and "pancakeRouter" params. But ONLY CHANGE the values (contracts), DO NOT CHANGE THE NAMES. It doesn't matter if it says "pancakeFactory" with ApeSwap Factory Contract. DO NOT CHANGE THE NAME, or the script will fail.

You can find this information directly in ApeSwap (ApeFactory and ApeRouter): https://apeswap.gitbook.io/apeswap-finance/smart-contracts

For example. you would have to change _"0xcA143Ce32Fe78f1f7019d7d551a6402fC5350c73"_ to _"0x0841BD0B734E4F5853f0dD8d7Ea041c241fb0Da6"_.

 <H2>How I use all these functions</H2>

 Easy piece. If you followed correctly the "Getting started" and the "Configuration File", you are ready to start.

 In your cmd (remember, you must be in the folder where .exe is), execute .exe --help or -h. You will find all these options I mentioned before.
```
 -h, --help                             show this help message and exit
  --spend SPEND, -s SPEND               Spender Symbol BNB or BUSD or USDT
  --gas GAS, -g GAS                     Gas
  --amount AMOUNT, -a AMOUNT            Amount to buy/sell
  --contract CONTRACT, -c CONTRACT      Contract of the Token
  --approval, -A                        Check allowance
  --sell                                Selling Process
  --buy                                 Buying Process
  --balances, -b                        Check your balances (optional)
  --price, -p                           Check token price (optional)
  --bpEnabled, -bp                      Check for Bot Protection (optional)
  --slippage SLIPPAGE, -sp SLIPPAGE     Slippage in percentage. Zero by default
  --liquidity LIQUIDITY, -lp LIQUIDITY  Minimium Token in LP to buy/sell
  --sellAll                             Sell all your contract balance tokens
  --checkHoneypot, -hp                  Check if the contract appears to be a honeypot
  --checkTaxes, -tax                    Check if the contract has buy/sell taxes.
  --maxBuyTax MAXBUYTAX                 Set maxBuyTax.
  --maxSellTax MAXSELLTAX               Set maxSellTax.
```
 So, first, the **REQUIRED** arguments are the CONTRACT (token you want to buy) and what pair you'll use.

 These are some examples of combinations. I will use as example the token CAKE (_0x0e09fabb73bd3ade0a17ecc321fd13a19e81ce82_) and my spend will be BNB. I want to buy CAKE using BNB. So, if:

 **You want to test if script works:**
```
 bscsniper.exe -c 0x0e09fabb73bd3ade0a17ecc321fd13a19e81ce82 -s BNB
```
 That's it. Your output will be:

  - Are you connected to BSC? Yes/No
  - If CAKE has a LP contract. If don't (as expected, before listing), the script will stay forever waiting until LP contract been created.
  - If yes, it will show you the liquidity, if any. If there is no liquidity (as expected, before listing, again), the script will stay forever waiting until liquidity is added (more than 10.000 token by default, if there is less than that, the script will stay waiting).

**You want to check your balances:**
```
 bscsniper.exe -c 0x0e09fabb73bd3ade0a17ecc321fd13a19e81ce82 -s BNB -b
```
  - You will see all information mentioned before (at first)...
  - ..and your balance for both. In this case your CAKE balance and your BNB balance.

**You want to check the price of the token (obviously, this one only works if there is liquidity):**
```
 bscsniper.exe -c 0x0e09fabb73bd3ade0a17ecc321fd13a19e81ce82 -s BNB -p
```
  - You will see all information mentioned before (at first)...
  - ..and the CAKE price in USD. 

**You want check and/or approve CAKE:**
```
 bscsniper.exe -c 0x0e09fabb73bd3ade0a17ecc321fd13a19e81ce82 -s BNB -A
```
  - The script will check if you've have approved the CAKE token. If yes, it will say "It's approved" and continues normally and then, you will see all information mentioned before (at first)
  - If the token is not approved, it will approved automatically for you. You will be able to see the transaction Id in the BSC Scan. Remember, this has a little fee on BSC network (around 0.12 USD)...
  - ...and then, you will see all information mentioned before (at first)...

**You want to BUY (obviously, this one only works if there is liquidity):**
```
bscsniper.exe -c 0x0e09fabb73bd3ade0a17ecc321fd13a19e81ce82 -s BNB -g 5 -a 0.1 --buy
```
 - As you can see, there are three new arguments:
    - `-g` or `--gas` is to specify the gas you want to spend in your transaction in GWEI. This is the same when you are gonna swap with your Metamask and you want to edit your gas, but this is easier and faster. Remember if you want to swap faster than anyone, you need to put a higher fee. Maybe 10 or 50, as you wish.
    - `-a` or `--amount` is the amount that you want to spend. For example if your are spending BNB, this is the amount in BNB that you want to spend, 10, 1, 0.1, 0.01 BNB. As you wish.
    - `--buy` is the trigger of the buy. If you put this flag, you are telling the script that you want to buy and it will execute the buy in BSC Scan. You will be able to see the transaction Id in the BSC Scan
 - You will see all information mentioned before (at first)...
 - You will be able to see when the script send the transaction to the BSC scan, and it will wait for the status (fail or success), and you will see it too.

**You want to SELL (obviously, this one only works if there is liquidity):**
```
bscsniper.exe -c 0x0e09fabb73bd3ade0a17ecc321fd13a19e81ce82 -s BNB -g 5 -a 10 --sell
```
 - It's the same buy process but instead using `--buy` you have to use **`--sell`**, and you have to change `-a` for the amount of tokens that to want to sell. For example if you want to sell "10 CAKE" you have to put `-a 10` and you will swap 10 CAKE for BNB. If you want to sell all your token balance, you have to use **`--sellAll`** function.
