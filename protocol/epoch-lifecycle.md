# Epoch Lifecycle

Surface Finance vaults run in cycles called **epochs**. Each epoch is a complete strategy cycle — from opening deposits, to deploying capital, to returning yield. Understanding the phases tells you when you can deposit, when your funds are at work, and when you can withdraw.

## Phases at a glance

| Phase | Can I deposit? | Can I withdraw? |
|---|---|---|
| Funding | ✓ Yes | ✓ Yes |
| Trading | ✗ No | ✗ No |
| Withdrawals Open | ✗ No | ✓ Yes |

---

## Phase 1 — Funding

The vault opens a **funding window** with a set start and end time. During this window:

- You can deposit your tokens and receive vault shares
- You can also withdraw freely if you already hold shares from a prior epoch
- The vault has not yet deployed capital — nothing is at risk yet

Deposit caps or access restrictions may apply. If your deposit is rejected, the vault may have reached its capacity for this epoch.

---

## Phase 2 — Trading

When the funding window closes, the vault enters its **active trading phase**. The strategy deploys capital to work the volatility of the underlying token.

During this phase:
- Deposits and withdrawals are **paused for all users**
- Your shares still represent your full proportional claim on the vault
- The strategy runs until it concludes — there is no action required from you

### How long does trading last?

Each epoch has a scheduled end date. Depending on the strategy, there may be a short period after the scheduled end before funds are fully settled and returned to the vault:

- Funds are typically returned within **72 hours** of the epoch end date
- In some cases, positions may remain open for up to **30 days** past the epoch end if market conditions warrant it

Withdrawals remain locked until funds are fully returned to the vault.

---

## Phase 3 — Withdrawals Open

Once the strategy concludes and funds are returned to the vault, the withdrawal window opens. The vault’s share price is updated to reflect the strategy’s net result — profit or loss.

At this point you can:
- **Withdraw** — redeem your shares for the updated token value
- **Roll over** — do nothing, and your shares automatically carry into the next epoch’s funding window

{% hint style="info" %}
You don’t need to take any action to roll over. If you leave your shares in the vault, they participate in the next epoch automatically.
{% endhint %}

{% hint style="warning" %}
If the strategy runs at a loss, the vault’s share price will be lower than when you deposited. All shareholders share this proportionally — there is no loss protection at the protocol level.
{% endhint %}
