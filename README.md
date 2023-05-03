# LazyMinting NFT Marketplace

## Dapp Demo 기본 정보
- Web Demo URL : https://lazy-mint-fe.vercel.app/
- Contract : https://goerli.etherscan.io/address/0x5a5eb29B037fA4b56D121e2E73D642d544B5Dce6#code
- Front-End Source : https://github.com/blockmonkey1992/Lazy-mint_FE
- Back-End Source : https://github.com/blockmonkey1992/Lazy-mint_BE

## Summary
본 프로젝트에서는 Opensea등에서 사용하는 NFT Lazyminting을 알아보기 위한 Project로 주로 사용하는 ERC-721 NFT에 대하여 Creator의 NFT 등록 시 비용 소모 없이 서명만을 통해 NFT를 등록하고, 구매자가 NFT를 구매할 때 서명 검증을 통해 실제로 NFT Minting 이루어지는 Dapp이다. NFT를 등록할 때 MongoDB를 통해 Board 정보의 Title, Des, Price등의 내용을 통해 MsgHash를 만들어 서명을 진행하고, Buyer가 나타나면 구매버튼을 클릭 할 때 SmartContract로 Voucher를 생성하면서 DB의 Title, Des, Price정보와 MsgHash정보를 검증하고 NFT를 민팅할 수 있다. 이를 통해 외부 공격자 또는 Service Provider의 악의적인 DB 위변조에 대하여 보완할 수 있으며 Creator가 등록한 정보 그대로를 데이터 무결성을 지키며 Minting이 가능하다. 또한 Blockchain Network를 활용함으로써 발생하는 Transaction 실패에 대한 가스비용 지불문제를 Static Call Method을 통해 EVM 정적 호출을 통해 사전확인 후 Transaction을 전송해 실패확률을 대폭 낮추었다. 또한 서명의 재사용문제를 Smart Contract에서 사용한 서명에 대한 정보를 mapping Data를 통해 관리하면서 서명 재사용 문제를 방지했다.


## Construction Skills
- Ethereum Goerli Test Network
- IPFS(nft.storage) - 분산형 파일저장 시스템으로 nft.storage를 사용했다.
- Solidity (8.15) - Smart Contract 개발언어로 8.15 최신버전을 사용했다.
- Hardhat & Ethers - Contract 개발 및 테스트 툴로 사용했다.
- Openzeppelin - Smart Contract Library
- React - Client Side
- Nodejs(Express) - Server Side
- MongoDB - NoSQL DB


## Application Architecture
![NFT](https://user-images.githubusercontent.com/66409384/180760130-0d272d18-8284-4d84-b6e5-08c269618646.png)


## Contract 구성

컨트렉트 내에는 기본적으로 Lazyminting, Minting, Set Locking, Minting Price Adjust(민팅가격조정), Emergency Withdrawal(비상출금) 등 의 기능을 포함하고 테스트 코드에서 확인이 가능하다.

실행방법
```
  npx hardhat test
```

![contract_Graph](https://user-images.githubusercontent.com/66409384/180267157-85d0bf2e-2cb6-48ef-bbd7-0e88bf1238fe.svg)
