# SafeStake-Mev-Boost-sidecar

> [Deployment process reference document : safestake-running-an-operator-node-on-going](https://github.com/ParaState/SafeStakeOperator/blob/main/safestake-running-an-operator-node-on-going.md)

---
## Additional steps:
### 1 [mev-boost config in .env](https://github.com/ParaState/SafeStakeOperator/blob/main/safestake-running-an-operator-node-on-going.md#use-your-own-configuration-1)
MEV_BOOST_RELAYS & GAS_LIMIT_INTEGER
```
# separated by ',' for multiple relays, such as MEV_BOOST_RELAYS=xxx,xxx,xxx
MEV_BOOST_RELAYS=https://0xafa4c6985aa049fb79dd37010438cfebeb0f2bd42b115b89dd678dab0670c1de38da0c4e9138c9290a398ecd9a0b3110@boost-relay-goerli.flashbots.net
#gas limit. [default: 30,000,000]
GAS_LIMIT_INTEGER=30000000

```

### 2 [Run your operator by docker-compose-operator-mev](https://github.com/ParaState/SafeStakeOperator/blob/main/safestake-running-an-operator-node-on-going.md#run-your-operator)
```
sudo docker compose -f  docker-compose-operator-mev.yml up -d
```

---
### TODO:
- test 默认gas-limit（dvf无需修改代码） [docker-compose-operator-mev](https://github.com/smallverse/SafeStakeOperator/blob/main/docker-compose-operator-mev.yml) , merge doc to dvf
- test 可设置gas-limit（dvf要修改代码支持gas设置） [docker-compose-operator-mev-dev](https://github.com/smallverse/SafeStakeOperator/blob/main/docker-compose-operator-mev-dev.yml) , merge doc & code to dvf


---
### Extended reading document:
- [What is MEV-Boost](https://docs.flashbots.net/flashbots-mev-boost/introduction)
- [MEV and Lighthouse](https://lighthouse-book.sigmaprime.io/builders.html)
- [Building an Ethereum Validator From Scratch](https://www.blocknative.com/blog/ethereum-validator-lighthouse-geth)
- [Guide | MEV-boost for Ethereum Staking](https://www.coincashew.com/coins/overview-eth/mev-boost)
