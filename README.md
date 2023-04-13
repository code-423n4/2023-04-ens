# ENS contest details
- Total Prize Pool: $114,850 USDC 
  - HM awards: $63,750 USDC 
  - QA report awards: $7,500 USDC 
  - Gas report awards: $3,750 USDC 
  - Judge awards: $14,600 USDC 
  - Lookout awards: $6,000 USDC 
  - Scout awards: $500 USDC 
  - Mitigation review contest: $18,750 USDC (*Opportunity goes to top 5 certified wardens based on placement in this contest.*)
- Join [C4 Discord](https://discord.gg/code4rena) to register
- Submit findings [using the C4 form](https://code4rena.com/contests/2023-04-ens-contest/submit)
- [Read our guidelines for more details](https://docs.code4rena.com/roles/wardens)
- Starts April 14, 2023 20:00 UTC 
- Ends April 21, 2023 20:00 UTC 

## Automated Findings / Publicly Known Issues

Automated findings output for the contest can be found [here](add link to report) within an hour of contest opening.

*Note for C4 wardens: Anything included in the automated findings output is considered a publicly known issue and is ineligible for awards.*

# Overview

# About ENS

ENS is a decentralised naming service built on top of Ethereum, and designed to resolve a wide array of resources including blockchain addresses, decentralised content, and user profile information.

Developer documentation can be found [here](https://docs.ens.domains/).

Information on existing ENS deployments can be found [here](https://docs.ens.domains/ens-deployments).

# Developer guide

## Quickstart

```
rm -Rf 2023-04-ens || true && git clone https://github.com/code-423n4/2023-04-ens.git -j8 --recurse-submodules && cd 2023-04-ens && nvm use 18.0 && yarn && REPORT_GAS=true yarn test
```

## Setup

```
git clone https://github.com/code-423n4/2022-11-ens
cd 2022-11-ens
yarn
```

## Running Tests

```
yarn test
```

# Scope

| Contract | SLOC | Purpose | Libraries used |  
| ----------- | ----------- | ----------- | ----------- |
| [https://github.com/code-423n4/2023-04-ens/blob/main/contracts/dnsregistrar/DNSClaimChecker.sol](contracts/dnsregistrar/DNSClaimChecker.sol) | 61 | Uses the DNSSEC oracle to verify DNS name claims | |
| [https://github.com/code-423n4/2023-04-ens/blob/main/contracts/dnsregistrar/OffchainDNSResolver.sol](contracts/dnsregistrar/OffchainDNSResolver.sol) | 190 | CCIP-read resolver contract to handle gasless DNS name resolution | [ERC165](https://github.com/OpenZeppelin/openzeppelin-contracts/blob/master/contracts/utils/introspection/ERC165.sol) |
| [https://github.com/code-423n4/2023-04-ens/blob/main/contracts/dnsregistrar/RecordParser.sol](contracts/dnsregistrar/RecordParser.sol) | 30 | Parses space delimited key-value strings from DNS TXT records | |
| [https://github.com/code-423n4/2023-04-ens/blob/main/contracts/dnsregistrar/DNSRegistrar.sol](contracts/dnsregistrar/DNSRegistrar.sol) | 165 | DNS registrar contract; permits registering DNS names in ENS, using the DNSSEC oracle | [ERC165](https://github.com/OpenZeppelin/openzeppelin-contracts/blob/master/contracts/utils/introspection/ERC165.sol) |
| [https://github.com/code-423n4/2023-04-ens/blob/main/contracts/dnssec-oracle/BytesUtils.sol](contracts/dnssec-oracle/BytesUtils.sol) | 243 | Byte string manipulation utils | |
| [https://github.com/code-423n4/2023-04-ens/blob/main/contracts/dnssec-oracle/RRUtils.sol](contracts/dnssec-oracle/RRUtils.sol) | 308 | DNS Resource-Record (RR) parsing utils | |
| [https://github.com/code-423n4/2023-04-ens/blob/main/contracts/dnssec-oracle/algorithms/RSASHA1Algorithm.sol](contracts/dnssec-oracle/algorithms/RSASHA1Algorithm.sol) | 35 | Implementation of the DNSSEC RSASHA1 algorithm | |
| [https://github.com/code-423n4/2023-04-ens/blob/main/contracts/dnssec-oracle/algorithms/EllipticCurve.sol](contracts/dnssec-oracle/algorithms/EllipticCurve.sol) | 283 | Implementation of ECDSA in Solidity | |
| [https://github.com/code-423n4/2023-04-ens/blob/main/contracts/dnssec-oracle/algorithms/P256SHA256Algorithm.sol](contracts/dnssec-oracle/algorithms/P256SHA256Algorithm.sol) | 31 | Implementation of the DNSSEC P256SHA256 algorithm | |
| [https://github.com/code-423n4/2023-04-ens/blob/main/contracts/dnssec-oracle/algorithms/ModexpPrecompile.sol](contracts/dnssec-oracle/algorithms/ModexpPrecompile.sol) | 28 | Utility contract for using the modexp/RSA precompile | |
| [https://github.com/code-423n4/2023-04-ens/blob/main/contracts/dnssec-oracle/algorithms/RSASHA256Algorithm.sol](contracts/dnssec-oracle/algorithms/RSASHA256Algorithm.sol) | 34 | Implementation of the DNSSEC RSASHA256 algorithm | |
| [https://github.com/code-423n4/2023-04-ens/blob/main/contracts/dnssec-oracle/algorithms/RSAVerify.sol](contracts/dnssec-oracle/algorithms/RSAVerify.sol) | 12 | RSA signature verification | |
| [https://github.com/code-423n4/2023-04-ens/blob/main/contracts/dnssec-oracle/digests/SHA1Digest.sol](contracts/dnssec-oracle/digests/SHA1Digest.sol) | 16 | Implementation of the DNSSEC SHA1 digest | |
| [https://github.com/code-423n4/2023-04-ens/blob/main/contracts/dnssec-oracle/digests/SHA256Digest.sol](contracts/dnssec-oracle/digests/SHA256Digest.sol) | 13 | Implementation of the DNSSEC SHA256 digest | |
| [https://github.com/code-423n4/2023-04-ens/blob/main/contracts/dnssec-oracle/DNSSECImpl.sol](contracts/dnssec-oracle/DNSSECImpl.sol) | 258 | A stateless DNSSEC oracle | |
| [https://github.com/code-423n4/2023-04-ens/blob/main/contracts/dnssec-oracle/SHA1.sol](contracts/dnssec-oracle/SHA1.sol) | 218 | Implementation of the SHA1 hash function in Solidity | |
| [https://github.com/code-423n4/2023-04-ens/blob/main/contracts/utils/NameEncoder.sol](contracts/utils/NameEncoder.sol) | 43 | Converts names from dot-separated to DNS binary format | |
| [https://github.com/code-423n4/2023-04-ens/blob/main/contracts/utils/HexUtils.sol](contracts/utils/HexUtils.sol) | 54 | Parses hex strings into bytes32 | |

## Out of scope

All files not listed above

# Additional Context

We implement userspace versions of SHA1 and SECP256p1. SHA1 is required for some DNSSEC zones; we don't choose the hash, the zone owner does. SECP256p1 is likewise used in many zones, including those hosted by cloudflare. 

The offchain DNS resolver uses [EIP 3668](https://eips.ethereum.org/EIPS/eip-3668) (CCIP-Read) and [ENSIP-10](https://docs.ens.domains/ens-improvement-proposals/ensip-10-wildcard-resolution) to support gasless DNS-based name resolution.

Slither does not work on this repository; we've reached out to the team in the past and nobody seems sure why not. If you find a workaround, please share it in the Discord.

## Scoping Details 
```
- If you have a public code repo, please share it here:  https://github.com/ensdomains/ens-contracts
- How many contracts are in scope?:   21
- Total SLoC for these contracts?:  2103
- How many external imports are there?: 5 
- How many separate interfaces and struct definitions are there for the contracts within scope?:  10
- Does most of your code generally use composition or inheritance?:   Composition
- How many external calls?:   0
- What is the overall line coverage percentage provided by your tests?:  90
- Is there a need to understand a separate part of the codebase / get context in order to audit this part of the protocol?:   false
- Please describe required context:   n/a
- Does it use an oracle?:  Others; DNS
- Does the token conform to the ERC20 standard?:  
- Are there any novel or unique curve logic or mathematical models?: DNSSEC, SHA1
- Does it use a timelock function?:  
- Is it an NFT?: 
- Does it have an AMM?:   
- Is it a fork of a popular project?: false  
- Does it use rollups?:   
- Is it multi-chain?:  
- Does it use a side-chain?: false
- Describe any specific areas you would like addressed. E.g. Please try to break XYZ.": Accuracy of DNSSEC implementation compared to the standard, any failures to check critical conditions.
```
