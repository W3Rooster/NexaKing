NXK Monthly Report — December 2025
This report documents architectural decisions, smart-contract reviews, deployment strategy refinements, Safe governance design, and launch-readiness work carried out for NXK during December 2025.
________________________________________
1. Deployment Tooling & Unified Guard System
•	Finalized and standardized unifiedGuard (env-guard.ts) across all scripts.
•	Added clear goals, introductions, allowed networks, and run instructions to:
o	launch
o	add-liquidity
o	post
o	token-limits
o	smoke tests
o	vesting (encode, release, check schedule)
o	verify-all
•	Evaluated dry-run concepts and safe execution patterns.
•	Standardized network auto-selection for payload generation.
•	Decided to convert console snippets into reusable scripts for all critical actions (e.g. exclusions, limits, pause, snipe blocks).
________________________________________
2. Safe Architecture & Wallet Strategy
•	Designed and finalized multi-Safe architecture:
o	SAFE_GOVERNANCE
o	SAFE_TREASURY
o	SAFE_LC (Liquidity Collector)
o	SAFE_LP_HOLDER
o	Separate Safes for ecosystem, marketing, airdrop, advisor
•	Confirmed:
o	Reusing EOAs across multiple Safes is acceptable
o	2-of-3 signer model is optimal for trust vs usability
•	Created new Safes and migrated roles cleanly.
•	Added all Safes to .env.profiles and deployment outputs.
•	Ensured no EOAs retain long-term power after deployment.
________________________________________
3. Liquidity Strategy & LP Governance
•	Finalized two-phase liquidity strategy:
1.	First liquidity added via EOA + Flashbots (MEV protection)
2.	Subsequent liquidity managed via SAFE_LC / SAFE_LP_HOLDER
•	Decided:
o	LP tokens always held by SAFE_LP_HOLDER
o	Liquidity Collector separated from LP holder
•	Removed reliance on Safe Delay Module (no longer supported in UI).
•	Selected third-party LP lock providers:
o	Team.Finance (preferred: fixed fee)
o	Unicrypt / PinkLock (reviewed)
•	Defined LP policy:
o	Lock 80–90% of each liquidity addition
o	Lock immediately after each add
o	Publish lock proofs publicly
•	Added Liquidity Transparency Policy to launch timeline.
________________________________________
4. Smart Contract Review (NXKToken.sol)
•	Conducted full, line-by-line audit of NXKToken.sol with focus on:
o	Pair-aware logic
o	Future-DEX compatibility
o	Investor trust / no red flags
•	Final decisions:
o	_transfer() fully pair-aware
o	Fees apply only on buy/sell, not wallet-to-wallet
o	Blacklist / sniper lists removed entirely
o	No max-tx feature (avoids rug optics)
o	Token contract itself excluded from limits in constructor
•	Defined immutable parameters:
o	LP tax: 0.25%
o	Dev tax: 0.25%
o	Total tax capped at 0.5% forever
•	Locked post-launch behavior:
o	No new fee exclusions after trading
o	LP wallet immutable after launch
o	Limits loosen-only
•	Removed pauseBypass entirely for maximum trust.
________________________________________
5. Vesting Architecture
•	Migrated fully to OpenZeppelin VestingWallet.
•	Finalized vesting parameters:
o	Team: 12-month cliff / 24-month duration
o	Advisor: 6 / 12
o	Stake: 6 / 12
•	Made vesting parameters configurable per network via .env.
•	Confirmed vesting Safes must be excluded from:
o	max buy
o	max wallet
o	fees
o	sniping
•	Clarified vesting release flows (no timelock needed).
•	Planned read-only scripts to verify vesting status at any time.
________________________________________
6. Deployment Safety & Anti-Mistake Guards
•	Added deploy.ts safety guard:
o	Prevents re-deployment if token already exists on mainnet
•	Removed liquidity creation from deploy.ts:
o	Liquidity always added after deployment
•	Implemented staleness checks:
o	Abort payloads older than defined threshold
•	Reviewed allowance usage and approval hygiene.
•	Integrated revoke.cash as mandatory post-deployment step.
________________________________________
7. DEX Indexing & Launch Timeline
•	Clarified DEX behavior:
o	DexScreener/DexTools index on first liquidity, not startTrading
•	Defined optimal launch timeline:
1.	Deploy contract
2.	Add liquidity (trading OFF)
3.	Verify LP + revoke approvals
4.	Flip startTrading = true
5.	DEX indexing
6.	Airdrop / growth
•	Ideal delay between liquidity & trading: 30–90 minutes
•	Created printable go / no-go checklist.
________________________________________
8. Monitoring, Analytics & Social Automation
•	Planned:
o	Dune Analytics dashboards
o	Telegram trade summary bot (daily, not per-trade spam)
•	Defined what should and should not be automated for optics.
•	Reviewed Etherscan write/read function coverage vs scripts.
________________________________________
9. Security & Operations
•	Hardened EOAs:
o	BitLocker
o	2FA
o	Revoke.cash
•	Documented procedures for:
o	Device theft
o	Safe recovery
•	Reviewed Windows vs Linux security tradeoffs (no migration yet).
________________________________________
Summary
December 2025 was a deep architecture and trust-hardening month for NXK.
Major outcomes:
•	Finalized Safe-only governance
•	Locked in fair, immutable token economics
•	Removed all red-flag features
•	Established a professional, repeatable launch and liquidity process
No mainnet launch occurred in this period. All work focused on security, correctness, and long-term credibility.

