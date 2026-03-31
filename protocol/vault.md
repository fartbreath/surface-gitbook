# How the Vault Works

Surface Finance vaults are the on-chain infrastructure that puts your memecoin holdings to work. Built on the ERC-4626 standard — a widely adopted standard for yield-bearing vaults — each vault connects your deposit to an institutional-grade trading strategy, with all accounting handled transparently on-chain. This page explains what happens to your tokens and how your position is tracked.

## Your position: vault shares

When you deposit into a Surface Finance vault, you receive **vault shares** — an ERC-20 token that represents your proportional ownership of the vault.

The value of each share is determined by the vault's **net asset value (NAV)** divided by the total number of shares in circulation:

$$\text{share price} = \frac{NAV}{\text{total shares}}$$

As the strategy generates returns, NAV increases, and each share becomes redeemable for more tokens than you deposited. If the strategy runs at a loss, the reverse is true — each share is worth fewer tokens.

**When you deposit**, the vault mints shares at the current share price:

$$\text{shares received} = \frac{\text{your deposit}}{\text{share price}}$$

**When you withdraw**, the vault burns your shares and returns the equivalent tokens:

$$\text{tokens returned} = \text{shares burned} \times \text{share price}$$

All share accounting is handled on-chain and is publicly verifiable.

## What happens to your tokens during trading

When the vault enters its active trading phase, the strategy takes custody of the vault's funds to execute trades. During this window:

- The vault's on-chain token balance will be zero or near-zero — this is expected
- Your shares still represent your proportional claim on the vault
- The vault tracks the full amount deployed into the strategy, so your share value is not affected by the custody transfer itself
- You cannot deposit or withdraw until the strategy concludes and funds are returned

Once the strategy concludes, the net proceeds (profit or loss) are returned to the vault contract and withdrawals reopen.

{% hint style="info" %}
The strategy is designed to generate yield from market volatility — not to predict direction. This means your tokens are actively working whether prices are moving up or down.
{% endhint %}

## Access and deposit limits

Some vaults may have:
- A **maximum deposit cap** — once reached, new deposits are not accepted until the next epoch
- A **whitelist requirement** — access may be restricted to approved addresses during early stages

{% hint style="warning" %}
Deposits and withdrawals are only available during their designated windows. During the active trading phase, **all deposits and withdrawals are paused**.
{% endhint %}
