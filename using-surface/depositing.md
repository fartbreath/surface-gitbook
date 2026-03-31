# Depositing

This page walks through how to deposit into a Surface Finance vault using the vault manager frontend.

## Before you start

- You need a wallet (e.g. MetaMask) connected to the correct network
- You need a balance of the vault's accepted ERC-20 token
- Deposits are only accepted during the **funding window** — check vault status before proceeding

{% hint style="info" %}
The vault dashboard shows the current phase. Look for the **"Funding"** phase indicator and the **"Deposits Open"** badge before attempting a deposit.
{% endhint %}

---

## Step 1 — Connect your wallet

Open the Surface Vault Manager and click **Connect Wallet** in the top right. Select your wallet provider and approve the connection request.

Once connected, load the vault contract address using the input at the top of the page and click **Load**.

---

## Step 2 — Check your position and vault status

Navigate to the **Status** tab to confirm:
- The vault is in the **Funding** phase
- **Deposits Open** badge is shown
- Your desired deposit amount is within the `maxDeposit` limit

You can also review:
- **Total Assets** — current vault NAV
- **Total Shares** — total supply of vault receipt tokens
- **Value per Share** — current NAV per share (the price you'll pay)

---

## Step 3 — Approve the asset

Navigate to the **Depositor** tab. Under **"1. Approve Asset"**, enter the amount you want to approve and click **Approve**.

This authorizes the vault contract to pull the token from your wallet. The approval transaction must confirm before you can deposit.

{% hint style="warning" %}
Approve at least the amount you intend to deposit. You only need to do this once per amount — if you plan to deposit more later, approve the larger amount now.
{% endhint %}

---

## Step 4 — Deposit

Under **"2. Deposit"**, enter the amount of tokens to deposit and click **Deposit**.

The vault will:
1. Pull the tokens from your wallet
2. Calculate your shares: $\text{shares} = \frac{\text{deposit} \times S}{NAV}$
3. Mint those shares to your address

A transaction link (Etherscan) will appear once the transaction is submitted. Wait for confirmation.

---

## After depositing

Your shares appear under **"My Shares"** in the Depositor tab. The **"Value per Share"** figure shows the current price — this will change as the strategy runs and NAV updates.

Once the vault enters the trading phase, your shares are locked until the epoch ends and funds are returned. You cannot deposit or withdraw during this window.

---

## Whitelist

Some vaults restrict access to whitelisted addresses. If your deposit is rejected with a whitelist error, contact the vault operator to request access.

---

## Fees

Fees are deducted by the trading strategy before funds are returned to the vault. The vault itself does not collect fees on-chain. The net P&L reflected in `returnFunds(amount)` already accounts for any strategy fees — your shares track the net NAV.
