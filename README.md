# testAuction-Audit
# **Test-Auction-Audit-Report**


# **Summary**

Test Auction smart contract security audit report performed by Build My Dapp (pvt) ltd.

The Test Auction Smart contract allows to auction a specific token with a starting and ending time limit.


# **In scope**

commit 2e22cbcfbcfb4a63466d27568c014ac3e58fda04

- Ownable.sol
- IERC20.sol
- TestAuction.sol https://github.com/AsfndAmin/testAuction-Audit


# **Findings**

In total, 10 issues were reported including:

- 5 high severity issues.
- 2 medium severity issues.
- 6 low severity issues.
- 1 owner privileges.

# **3x Error (severity)**

-
# **High**

1. Reentrancy in Auction.refundAll().

1. Auction.setCaps() ignores return value.

1. Auction.refundAll() ignores return value.

1. Auction.claimTokens() ignores return value.

1. Auction.depositAuction() ignores return value.

-
# **Medium**

1. Reentrancy in Auction.claimTokens().

1. Reentrancy in Auction.depositAuction().

-
# **Low**

1. Auction.setCaps() should emit an event .

1. Auction.constructor().\_offeringToken lacks a zero-check.

1. Auction.refundAll() has external calls inside a loop.

1. Auction.setCaps() uses timestamp for comparisons.

1. Auction.checkConditions() uses timestamp for comparisons.

1. Auction.checkConditions() compares to a boolean constant.

-
# **minor observation**

1. Pragma version^0.8.0 allows old versions.
2. solc-0.8.9 is not recommended for deployment.
3. renounceOwnership() should be declared external.

-
# **owner privileges**

1. Owner can change supplyToDistribute.
2. Owner can change softCap.

# **Code snippet**

Line 53

Line 62

Line 79

Line 112

# **Recommendation**

- Apply the check-effects-interactions pattern.
- Use SafeERC20, or ensure that the transfer/transferFrom return value is checked.
- Apply the check-effects-interactions pattern.
- Favor pull over push strategy for external calls(low).


# **Conclusion**

The smart contract has been audited and 5 high severity issues found that needs to be resolved before deploying.
Two medium severity issue also found and is recommended to be resolved. There are some low severity issues and some minor mistakes
and have been pointed in the report.
