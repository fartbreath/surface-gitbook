# Security & Transparency

Bringing institutional-grade strategies on-chain means holding the same standards institutions expect: transparent accounting, audited contracts, and clearly defined rules. This page explains the key properties you should understand as a depositor.

## Your shares vs. your capital

It’s important to understand the distinction between two things:

**Your vault shares** are held in your own wallet. Surface Finance never holds your shares on your behalf, and only you can redeem or transfer them.

**Your deposited capital**, during the active trading phase, is managed by Surface Finance’s professional trading operation. This is the core of the product — an institutional-grade team actively managing your tokens to generate yield from market conditions. The vault contract enforces the rules around when and how capital can be moved, and all fund movements are recorded on-chain.

Think of it as the on-chain equivalent of a managed fund: your position is yours, your capital is working.

## Open source contracts

The Surface Finance vault contracts are open source and publicly verifiable. The vault is built on the ERC-4626 standard using audited OpenZeppelin components, including:

- **ERC-4626** — the standardized on-chain vault interface
- **ReentrancyGuard** — prevents reentrancy attacks on all fund-moving functions
- **SafeERC20** — ensures safe token transfer behavior across all ERC-20 tokens

## What you can verify on-chain

All vault activity is recorded on-chain and publicly readable:

| What you can check | Where to look |
|---|---|
| Current vault balance (total assets) | `totalAssets()` on the vault contract |
| Your share balance | Your wallet's ERC-20 balance of the vault token |
| Your shares' current value | `convertToAssets(yourShares)` |
| Whether deposits are open | `isFunding()` |
| Whether the epoch is active | `isInEpoch()` |
| Current epoch timing | `getCurrentEpochInfo()` |

## Risk disclosures

- **Counterparty risk** — during the trading phase, capital is deployed by the trading operation. Returns depend on the performance and integrity of that operation. Review Surface Finance’s track record and team before depositing significant capital.
- **Strategy risk** — the strategy may return less than deposited. Losses are shared proportionally across all shareholders.
- **Smart contract risk** — despite audits and use of established libraries, smart contracts can contain bugs. Only deposit what you are comfortable putting at risk.
- **Liquidity risk** — during the active trading phase, withdrawals are paused. You will not be able to exit until the epoch concludes.

{% hint style="info" %}
The vault contract source is available in the Surface Vault GitHub repository for independent review.
{% endhint %}
