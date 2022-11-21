<!-- START doctoc generated TOC please keep comment here to allow auto update -->
<!-- DON'T EDIT THIS SECTION, INSTEAD RE-RUN doctoc TO UPDATE -->
**Table of Contents**  *generated with [DocToc](https://github.com/thlorenz/doctoc)*

- [Day 3 Exercises](#day-3-exercises)
  - [Best Practice for Testing Smart Contracts](#best-practice-for-testing-smart-contracts)
    - [Best Practice for Testing Smart Contracts: What Is Smart Contract Testing?](#best-practice-for-testing-smart-contracts-what-is-smart-contract-testing)
    - [Best Practice for Testing Smart Contracts: Why Is It Important To Test Smart Contracts?](#best-practice-for-testing-smart-contracts-why-is-it-important-to-test-smart-contracts)
    - [Best Practice for Testing Smart Contracts: Automated Testing For Smart Contracts](#best-practice-for-testing-smart-contracts-automated-testing-for-smart-contracts)
    - [Best Practice for Testing Smart Contracts: Manual Testing For Smart Contracts](#best-practice-for-testing-smart-contracts-manual-testing-for-smart-contracts)
    - [Best Practice for Testing Smart Contracts: Testing Vs. Formal Verification](#best-practice-for-testing-smart-contracts-testing-vs-formal-verification)
  - [Useful Resources for Your Next Steps](#useful-resources-for-your-next-steps)
    - [Useful Resources for Your Next Steps: Solidity Resources](#useful-resources-for-your-next-steps-solidity-resources)
    - [Useful Resources for Your Next Steps: Chainlink Resources](#useful-resources-for-your-next-steps-chainlink-resources)
    - [Useful Resources for Your Next Steps: Crypto Twitter Accounts Worth Following](#useful-resources-for-your-next-steps-crypto-twitter-accounts-worth-following)

<!-- END doctoc generated TOC please keep comment here to allow auto update -->

# Day 3 Exercises

![image](https://user-images.githubusercontent.com/11134288/203155605-f91ef525-428f-4ab6-bc3b-6a974999c62a.png)

---

## Best Practice for Testing Smart Contracts

The third and last day of the BootCamp had no exercises. Instead the main item presented during this day was how to go about writing a good smart contract. This means everything from what is the difference between bugs and vulnerabilities or how to go about finding an audit company to audit your smart contract. It is unclear where to find the course materials for this section of the third day. Below you can find something similar extracted from the official Ethereum documentation: [https://ethereum.org/en/developers/docs/smart-contracts/testing/](https://ethereum.org/en/developers/docs/smart-contracts/testing/)

---

### Best Practice for Testing Smart Contracts: What Is Smart Contract Testing?

Smart contract testing means performing detailed analysis and evaluation of a smart contract to assess the quality of its source code during the development cycle. Testing a smart contract makes it easier to identify bugs and vulnerabilities and reduces the possibility of software errors that could lead to costly exploits.

Smart contract testing takes many forms, with different methods offering benefits. Strategies for testing Ethereum smart contracts can be classified into two broad categories: automated testing and manual testing.

**Automated testing**

Automated testing involves using automated tools to carry out scripted testing of smart contracts. This technique relies on automated software that can execute repeated tests to find defects in smart contracts.

Automated testing is efficient, uses fewer resources, and promises higher levels of coverage than manual analysis. Automated testing tools can also be configured with test data, allowing them to compare predicted behaviors with actual results.

**Manual testing**

Manual testing is human-aided and involves an individual who executes testing steps manually. Code audits, where developers and/or auditors, go over every line of contract code, are an example of manual testing for smart contracts.

Manual testing of smart contracts requires considerable skill and a considerable investment of time, money, and effort. Moreover, manual testing can sometimes be susceptible to the problems of human error.

However, applying manual testing to smart contracts can also be beneficial. Code audits harness human intelligence to find defects in contract code that might go undetected during automated testing.

Manual-testing your smart contracts can also reveal vulnerabilities that exist outside the code, but can still affect it. For example, a smart contract audit can discover vulnerabilities arising from flawed interaction with off-chain components.

---

### Best Practice for Testing Smart Contracts: Why Is It Important To Test Smart Contracts?

Testing smart contracts is important for the following reasons:

1. Smart contracts are high-value applications:

    Smart contracts often deal with high-value financial assets, especially in industries like [decentralized finance (DeFi)](https://ethereum.org/en/defi/), and valuable items, such as [non-fungible tokens (NFTs)](https://ethereum.org/en/nft/). As such, minor vulnerabilities in smart contracts can and often lead to massive, irrecoverable losses for users. Comprehensive testing can, however, expose errors in smart contract code and reduce security risks before deployment.

2. Smart contracts are immutable

    Smart contracts deployed in the [Ethereum Virtual Machine (EVM)](https://ethereum.org/en/developers/docs/evm/) are immutable by default. While traditional developers may be used to fixing software bugs after launching, Ethereum development leaves little room for patching security flaws once a smart contract is live on the blockchain.

    While upgradeability mechanisms for smart contracts, such as proxy patterns, these can be difficult to implement. Besides reducing immutability and introducing complexity, upgrades often demand complex governance processes.

    For the most part, upgrades should be considered a last resort and avoided unless necessary. Detecting potential vulnerabilities and flaws in your smart contract during the pre-launch phase reduces the need for a logic upgrade

---

### Best Practice for Testing Smart Contracts: Automated Testing For Smart Contracts

1. _Functional testing:_

    Functional testing verifies the functionality of a smart contract and provides assurance that each function in the code works as expected. Functional testing requires understanding how your smart contract should behave in certain conditions. Then you can test each function by running computations with selected values and comparing the returned output with the expected output.

    Functional testing covers three methods: **unit testing**, **integration testing**, and **system testing**.

    - **Unit testing:**

        Unit testing involves testing individual components in a smart contract for correctness. A unit test is simple, quick to run, and provides a clear idea of what went wrong if the test fails.

        Unit tests are crucial for smart contract development, especially if you need to add new logic to the code. You can verify the behavior of each function and confirm that it executes as intended.

        Running a unit test often requires creating assertions—simple, informal statements specifying requirements for a smart contract. Unit testing can then be used to test each assertion and see if it holds true under execution.

        Examples of contract-related assertions include: i). "Only the admin can pause the contract"; ii). "Non-admins cannot mint new tokens"; iii). "The contract reverts on errors".

    - **Integration testing:**

        Integration testing is a level higher than unit testing on the testing hierarchy. In integration testing, individual components of the smart contract are tested together.

        This approach detects errors arising from interactions between different components of a contract or across multiple contracts. You should use this method if you have a complex contract with multiple functions or one that interfaces with other contracts.

        Integration testing can be useful for ensuring that things like [inheritance](https://docs.soliditylang.org/en/v0.8.12/contracts.html#inheritance) and dependency injection work properly.

    - **System testing:**

        System testing is the final phase of functional testing for smart contracts. A system evaluates the smart contract as one fully integrated product to see if it performs as specified in the technical requirements.

        You can think of this stage as checking the end-to-end flow of your smart contract from a user’s point of view. A good way to perform system testing on a smart contract is to deploy it on a production-like environment, such as a [testnet](https://ethereum.org/en/developers/docs/networks/#ethereum-testnets) or [development network](https://ethereum.org/en/developers/docs/development-networks/).

        Here, end-users can perform trial runs and report any issues with the contract’s business logic and overall functionality. System testing is important because you cannot change code once the contract is deployed in the main EVM environment

2. _Static/dynamic analysis_

    Static analysis and dynamic analysis are two automated testing methods for evaluating the security qualities of smart contracts. Both techniques, however, use different approaches for finding defects in contract code.

    - **Static analysis**:

        Static analysis examines the source code or bytecode of a smart contract before execution. This means you can debug contract code without actually running the program. Static analyzers can detect common vulnerabilities in Ethereum smart contracts and aid compliance with best practices.

    - **Dynamic analysis**:

        Dynamic analysis techniques require executing the smart contract in a runtime environment to identify issues in your code. Dynamic code analyzers observe contract behaviors during execution and generate a detailed report of identified vulnerabilities and property violations.

        Fuzzing is an example of a dynamic analysis technique for testing contracts. During fuzz testing, a fuzzer feeds your smart contract with malformed and invalid data and monitors how the contract responds to those inputs.

        Like any program, smart contracts rely on inputs provided by users to execute functions. And, while we assume users will provide correct inputs, this may not always be the case.

        In some cases, sending incorrect input values to a smart contract can cause resource leaks, crashes, or worse, lead to unintended code execution. Fuzzing campaigns identify such problems beforehand, allowing you to eliminate the vulnerability

---

### Best Practice for Testing Smart Contracts: Manual Testing For Smart Contracts

1. _Code audits_

    A code audit is a detailed evaluation of a smart contract's source code to uncover possible failure-points, security flaws, and poor development practices. While code audits can be automated, we refer to human-aided code analysis here.

    Code audits require an attacker mindset to map out possible attack vectors in smart contracts. Even if you run automated audits, analyzing every line of source code is a minimum requirement for writing secure smart contracts.

    You can also commission a security audit to give users higher assurances of smart contract safety. Audits benefit from extensive analysis performed by cybersecurity professionals and detect potential vulnerabilities or bugs that could break the smart contract functionality.

2. _Bug bounties_

    A bug bounty is a financial reward given to an individual who discovers a vulnerability or bug in a program's code and reports to developers. Bug bounties are similar to audits since it involves asking others to help find defects in smart contracts. The major difference is that bug bounty programs are open to the wider developer/hacker community.

    Bug bounty programs often attract a broad class of ethical hackers and independent security professionals with unique skills and experience. This may be an advantage over smart contract audits that mainly rely on teams who may possess limited or narrow expertise

---

### Best Practice for Testing Smart Contracts: Testing Vs. Formal Verification

While testing helps confirm that a contract returns the expected results for some data inputs, it cannot conclusively prove the same for inputs not used during tests. Testing a smart contract cannot guarantee "functional correctness", meaning it cannot show that a program behaves as required for all sets of input values and conditions.

As such, developers are encouraged to incorporate **formal verification** into their approach for assessing the correctness of smart contracts. Formal verification uses [formal methods](https://www.brookings.edu/techstream/formal-methods-as-a-path-toward-better-cybersecurity/) — mathematically rigorous techniques for specifying and verifying software.

Formal verification is considered important for smart contracts because it helps developers formally test assumptions relating to smart contracts. This is done by creating formal specifications that describe a smart contract's properties and verifying that a formal model of the smart contract matches the specification. This approach increases confidence that a smart contract will only execute functions as defined in its business logic and nothing else.

[More on formal verification for smart contracts](https://ethereum.org/en/developers/docs/smart-contracts/formal-verification)

---

## Useful Resources for Your Next Steps

Here are some educational resources that the BootCamp team think you might find useful.

---

### Useful Resources for Your Next Steps: Solidity Resources

On-line learning platforms and Youtube channels:
* [CryptoZombies](https://cryptozombies.io/)
* [Moralis Academy](https://academy.moralis.io/)
* [Dapp University](https://www.dappuniversity.com/)
* [Chainshot](https://www.chainshot.com/)
* [Freecodecamp](https://www.youtube.com/c/Freecodecamp)

---

### Useful Resources for Your Next Steps: Chainlink Resources

On-line resources and videos:
* [Patrick Collins tutorials](https://www.youtube.com/c/PatrickCollins):
    - [Blockchain, Solidity, and Full Stack Web3 Development with JavaScript – 32-Hour Course](https://www.youtube.com/watch?v=gyMwXuJrbJQ)
    - [Solidity, Blockchain, and Smart Contract Course – Beginner to Expert Python Tutorial](https://www.youtube.com/watch?v=M576WGiDBdQ)
* [Chainlink YouTube](https://www.youtube.com/channel/UCnjkrlqaWEBSnKZQ71gdyFA)
* [Engineering tutorials](https://www.youtube.com/watch?v=9uUk9neDqcM&list=PLVP9aGDn-X0QwJVbQvuKr-zrh2_DV5M6J)
* [Chainlink website](https://chain.link/)
* [Developer Resources Developer Documentation](https://chain.link/developer-resources)
* [Chainlink Discord](https://discord.com/invite/chainlink)
* [Chainlink Github](https://github.com/smartcontractkit/chainlink)

---

### Useful Resources for Your Next Steps: Crypto Twitter Accounts Worth Following

* Andreas Antonopolous [@aantonop](https://twitter.com/aantonop) (Bitcoin educator)
* Vitalik Buterin [@VitalikButerin](https://twitter.com/VitalikButerin) and Ethereum Foundation [@ethdotorg](https://twitter.com/ethdotorg)
* Sergey Nazarov [@SergeyNazarov](https://twitter.com/SergeyNazarov) and Chainlink [@chainlink](https://twitter.com/chainlink)
* Delphi Labs [@delphi_labs](https://twitter.com/delphi_labs) and Messari [@MessariCrypto](https://twitter.com/MessariCrypto) (blockchain research)
* Punk6529 [@punk6529](https://twitter.com/punk6529) (NFT and Metaverse educator)
* ChainlinkGod [@ChainLinkGod](https://twitter.com/ChainLinkGod) (decentralised oracles)
* Marc Zeller of AAVE [@lemiscate](https://twitter.com/lemiscate) (DeFi)
* DeFi Dad [@DeFi_Dad](https://twitter.com/DeFi_Dad) (DeFi, on-chain analytics)
* Laura Shin [@laurashin](https://twitter.com/laurashin) (crypto journalist, also author of the [Unchained](https://unchainedpodcast.com/) podcast)

---
