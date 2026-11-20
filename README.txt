PUMP CALLOUT HUNTER — AUDITED CANDIDATE BUILD

This is a replacement candidate for the current index.html. Do not delete the old repository.

WHAT WAS CHANGED
- Uses PumpDev's documented control acknowledgements. A token counts as tracked only after the server returns type=subscribed and includes that mint in keys.
- Sends token subscriptions in batches instead of one WebSocket control message per mint.
- Prioritizes newest launches and caps the waiting queue; old queued launches are marked skipped instead of silently filling the queue.
- Shows dashes, not zeroes, for tokens that have not actually been subscribed to.
- Shows the number of received BUY/SELL events separately.
- Uses traderPublicKey for unique BUY wallets.
- Uses solAmount when present; quoteAmount is used as SOL only when quoteMint is wrapped SOL. Unknown quote currency does not get added to net SOL.
- Rotates DEX Screener polling across the token list instead of repeatedly polling only the first eight.
- Labels drawdown honestly as change from the first DEX snapshot observed by this browser, not the true ATH.
- Re-subscribes recent tokens after a WebSocket reconnect.
- Shows a warning that the anonymous PumpDev tier allows 5 live subscriptions, 1 connection per IP and 1,000 trade messages/month (IPs that used the old keyless feed before 2026-10-27 may retain 10k).

TEST PLAN BEFORE REPLACING LIVE FILE
1. Upload index.html to a separate test repository or temporarily keep the current production file backed up.
2. Open only one app tab/device per public IP. Do not leave the PC and iPhone connected simultaneously on the same Wi-Fi.
3. Check that "Pretplate potvrđene" rises only after a PumpDev subscribed ACK.
4. Check that a tracked token changes from "Čeka red" to "Aktivno · potvrđeno".
5. Confirm the trade counter increases and BUY/SELL values match the corresponding mint.
6. Wait for the 90-second sample to finish.
7. Confirm DEX pair count changes over time as the round-robin scan progresses.
8. Repeat once on iPhone, with the PC app closed.

LIMITATIONS
- This is a client-side browser app. It stops when the browser suspends/closes the page.
- Anonymous feed is per IP; a second device or tab on the same public IP can conflict with the one-connection limit.
- 5 active token subscriptions and the monthly trade quota mean it cannot monitor every launch. It prioritizes recent launches; skipped tokens are visibly marked.
- DEX Screener pool data appears only after a pool is indexed.
- A DEX snapshot is not a rug-pull audit; volume and liquidity can be manipulated.
- No wallet, private key, auto-buy, or auto-publishing.
