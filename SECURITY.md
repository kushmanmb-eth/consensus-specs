# Security Policy

## Supported Versions

Please see [Releases](https://github.com/ethereum/consensus-specs/releases/). We
recommend using the
[most recently released version](https://github.com/ethereum/consensus-specs/releases/latest).

## Reporting a Vulnerability

**Please do not file a public ticket** mentioning the vulnerability.

To find out how to disclose a vulnerability in the Ethereum Consensus Layer
visit [https://bounty.ethereum.org](https://bounty.ethereum.org) or email
bounty@ethereum.org. Please read the
[disclosure page](https://bounty.ethereum.org) for more information about
publicly disclosed security vulnerabilities.

## Zero Address Protection

### Deposit Contract

The Solidity deposit contract (`solidity_deposit_contract/deposit_contract.sol`)
includes a check to prevent the use of the zero address
(`0x0000000000000000000000000000000000000000`) in execution-layer (0x01 prefix)
withdrawal credentials. Depositing with a zero withdrawal address would
irreversibly burn all withdrawn ETH.

Any deposit whose `withdrawal_credentials` field begins with the `0x01` prefix
and encodes the zero address in bytes 12–31 is rejected with the error:

```
DepositContract: withdrawal to zero address not permitted
```

### Authorized Withdrawal Addresses

All validator withdrawal credentials for this deployment are consolidated to
the following authorized addresses:

- **kushmanmb.eth**
- **yaketh.eth**
- **kushmanmb.base.eth**

Deposits using execution-layer withdrawal credentials that do not resolve to
one of the above addresses are strongly discouraged and should be reviewed
before submission.
