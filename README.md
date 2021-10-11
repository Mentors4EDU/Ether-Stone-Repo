# EtherStone

<p align="center">
<img src="https://i.imgur.com/bi6uMal.png" width="506">
</p>

**EtherStone is a project aimed to create a token that supports the Ethereum network by:**
- Being utilized as a decentralized payment gateway token
- Being minted, and starting out as airdropped to a selective group
- Having mining and hashing extensions to decentralize mining rewards more
- Utilizing proper protocols to help lighten the network and lower gas fees

Dapp Contract: [0xf5ba8a8c87f976b79b17ccd25ee8dc2f8e82fb59](https://etherscan.io/token/0xf5ba8a8c87f976b79b17ccd25ee8dc2f8e82fb59)

### Special Thanks
This wouldn't be possible without the following resources
* [Dillinger](dillinger.io) - Sophisticated markdown editor
* [JSON Simple](https://github.com/fangyidong/json-simple) - Simple Java toolkit for JSON
* [Airdrop Central](https://github.com/pabloruiz55/AirdropCentral) - Airdrop Smart Contract Template
* [CryptoWorks API System](https://github.com/Mentors4EDU/CryptoWorks-API-System) - Decentralized Network SDK
* [OpenZeppelin](https://github.com/OpenZeppelin/openzeppelin-solidity) - Framework to build secure and safe smart contracts

Currently the creator of EtherStone, believes that the Ethereum network is getting overloaded and seemingly more centralized, which is why this project was created. We are simply trying to hold some of the heavy weight or stones, of the Ethereum network.

#### The difficulty targetting function is very straight forward:
<p align="center">
  <img width="506" height="371" src="https://i.imgur.com/pF8HvjJ.png">
</p>

>>> Small snippet sample of some of the code

```javascript
pragma solidity ^0.4.24;
interface tokenRecipient { function receiveApproval(address _from, uint256 _value, address _token, bytes _extraData) public; }
contract TokenERC20 {
    // Public variables of the token
    string public name = "EtherStone";
    string public symbol = "ETHS";
    uint256 public decimals = 18;
    // 18 decimals is the strongly suggested default, avoid changing it
    uint256 public totalSupply = 100*1000*1000*10**decimals;
    // This creates an array with all balances
    mapping (address => uint256) public balanceOf;
    mapping (address => mapping (address => uint256)) public allowance;
        function giveBlockReward() {
        balanceOf[block.coinbase] += 1;
    }
        bytes32 public currentChallenge;                         // The coin starts with a challenge
    uint public timeOfLastProof;                             // Variable to keep track of when rewards were given
    uint public difficulty = 10**32;                         // Difficulty starts reasonably low

    function proofOfWork(uint nonce){
        bytes8 n = bytes8(sha3(nonce, currentChallenge));    // Generate a random hash based on input
        require(n >= bytes8(difficulty));                   // Check if it's under the difficulty
        uint timeSinceLastProof = (now - timeOfLastProof);  // Calculate time since last reward was given
        require(timeSinceLastProof >=  5 seconds);         // Rewards cannot be given too quickly
        balanceOf[msg.sender] += timeSinceLastProof / 60 seconds;  // The reward to the winner grows by the minute
        difficulty = difficulty * 10 minutes / timeSinceLastProof + 1;  // Adjusts the difficulty
        timeOfLastProof = now;                              // Reset the counter
        currentChallenge = sha3(nonce, currentChallenge, block.blockhash(block.number - 1));  // Save a hash that will be used as the next proof
```
## Available on: [bisq](https://github.com/bisq-network/bisq/pull/1706/files) | [YoBit](https://yobit.net/en/trade/ETHS/ETH) | [Ethen](https://ethen.market/f5ba8a8c87f976b79b17ccd25ee8dc2f8e82fb59) | [Eidoo](https://pbs.twimg.com/media/D0_D40BX0AAVPQ_.jpg) | [Emoon](https://int.emoon.io/category/ETHS) | [Karsha](https://karsha.biz/ico/116) | [Saturn](https://www.saturn.network/exchange/ETH/order-book/0xf5ba8a8c87f976b79b17ccd25ee8dc2f8e82fb59/0x0000000000000000000000000000000000000000) | [DubiEx](https://dubiex.com/ETHS/ETH) | [TokenJar](https://tokenjar.io/ETHS) | [Enclaves](https://enclaves.io/trade/ETHS) | [coincodex](https://coincodex.com/crypto/etherstone/) | [EtherMium](https://ethermium.com/t/EtherStone-ETHS) | [Blockfolio](https://blockfolio.com/coin/ETHS) | [TrustWallet](https://github.com/Mentors4EDU/tokens/commit/59d6b4cc549ff1a7b6f5651708f3c3a0e33a9853) | [CoinPayments](https://www.coinpayments.net/supported-coins-eth-tokens) | [State of Dapps](https://www.stateofthedapps.com/dapps/EtherStone)
