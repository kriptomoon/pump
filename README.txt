PUMP CALLOUT HUNTER — CLEAN REPOSITORY BUILD

UPLOAD
1. Create a NEW empty GitHub repository (Public).
2. Upload index.html from this folder to the repository root.
3. Settings > Pages > Deploy from a branch > main > /(root) > Save.
4. Wait for deployment, then open the GitHub Pages URL and hard-refresh (Ctrl+Shift+R).

DATA SOURCES
- PumpDev WebSocket: wss://pumpdev.io/ws (new token + trade subscriptions).
- DexScreener public API: token pools / liquidity / 5m volume and buy/sell counters.
- No wallet, private key, API key, paid feed, auto-buy or auto-callout.

IMPORTANT LIMITATIONS
- PumpDev anonymous tier is published as 5 subscriptions and 10,000 trade messages/month.
- DEX Screener data appears only when a pool is indexed; a missing pool is NOT zero liquidity.
- DEX 5m buy/sell counts are pool aggregates, not a wallet-unique count.
- Unique buyer count in the early trade sample depends on traderPublicKey/user being present.
- Price drop is measured only from the first DEX snapshot observed by this page, not the true launch high.
- This is a screening aid, not a honeypot/rug-pull audit or a guarantee of profitable trades.
- A browser tab must remain open. No backend, VPS, or background monitoring.

FILTER DEFAULTS
BUY share >= 60%, unique buyers >= 5, net SOL >= 0.3, liquidity >= $5,000,
max observed drawdown 20%, minimum 8 trade events.
These are starting filters and can be changed in the UI.

The old repository is not deleted by this ZIP. First verify the new Pages site works.
Only then delete the old repository if you still want to remove it.
