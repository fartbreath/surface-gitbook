# Withdrawing

This page explains how and when you can withdraw from a Surface Finance vault.

## When can you withdraw?

Withdrawals are available during two windows:

| Vault phase | Withdrawals |
|---|---|
| Idle | ✓ Open |
| Scheduled (before funding starts) | ✓ Open |
| Funding | ✓ Open |
| Trading (funds in vault) | ✗ Locked |
| Trading (funds custodied) | ✗ Locked |
| Unwinding | ✗ Locked |
| Withdrawals Open (post-epoch) | ✓ Open |

{% hint style="warning" %}
Withdrawals are **locked** any time the vault is in an active epoch or funds are custodied by the trader. The **"Withdrawals Locked"** badge in the Status tab indicates this state.
{% endhint %}

---

## Withdraw vs. Redeem

The vault supports two methods to exit your position:

**Withdraw by asset amount** — specify how many underlying tokens you want to receive. The vault calculates and burns the corresponding shares.

$$\text{shares burned} = \frac{\text{assets requested} \times S}{NAV}$$

**Redeem by share amount** — specify how many vault shares to burn. The vault calculates and returns the corresponding underlying tokens.

$$\text{assets returned} = \frac{\text{shares burned} \times NAV}{S}$$

Both methods result in the same outcome — choose whichever is more convenient.

---

## How to withdraw

1. Connect your wallet and load the vault contract address on the vault manager frontend
2. Navigate to the **Depositor** tab
3. Confirm the **"Withdrawals Open"** badge is shown in the Status tab
4. Under **"Withdraw Assets"**, enter the asset amount and click **Withdraw**  
   — or under **"Redeem Shares"**, enter the share amount and click **Redeem**
5. Confirm the transaction in your wallet
6. Once confirmed, your tokens will appear in your wallet

---

## Withdrawing at a loss

If the strategy experienced a loss during the epoch, the NAV per share will be lower than at deposit. Withdrawing after a loss-making epoch means you receive fewer underlying tokens than you deposited — the loss is pro-rated across all shareholders. The vault contract does not offer any loss protection at the protocol level.

---

## Rolling over to the next epoch

If you do not withdraw after an epoch ends, your shares automatically roll over into the next epoch. When the owner calls `startEpoch` again, the vault re-enters the funding phase and your shares continue to participate.

There is no action required to roll over — simply leave your shares in the vault.

---

## Emergency / paused state

If the vault is paused by the owner, all withdrawals are temporarily blocked. This is a safety mechanism for emergencies. Monitor vault events (`Paused`, `Unpaused`) or the vault status dashboard for state changes.
