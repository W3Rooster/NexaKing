NXK Monthly Report — November 2025
________________________________________
Governance & Wallet Infrastructure
•	Activated and tested Safe multisig accounts (mainnet & Sepolia).
•	Separated Safe accounts per network (mainnet vs Sepolia).
•	Enabled MetaMask Smart Account usage for Safe interaction.
•	Documented Safe operations:
o	ETH transfers
o	Token transfers (including dust amounts)
o	Recovery and security setup
•	Installed and used revoke.cash to review and revoke wallet permissions.
•	Reviewed adding additional owners to multisig setups.
________________________________________
Smart Contract Development & Testing
•	Worked on anti-MEV protections (design + partial implementation).
•	Reviewed and tested isExcludedFromFee logic (including pair behavior).
•	Added exclusion tests to pool-check-reserve.ts.
•	Reduced and reviewed maxAmountGlobal logic.
•	Analyzed max-buy / max-wallet pair restrictions and removal strategy.
•	Implemented and refined timelock-based execution flow (OZ pattern).
•	Rewrote apply-timelock.ts.
•	Reviewed and tested:
o	Transfer delay
o	Snipe block logic
o	Temporary paused-bypass for liquidity
•	Evaluated blacklist removal edge cases.
________________________________________
Environment & Deployment Tooling
•	Created automatic .env profile system:
o	mainnet
o	sepolia
o	fork
•	Clarified number and purpose of .env.profile files.
•	Added env-guard.ts (unified guard) and integrated it into:
o	add-liquidity
o	post
o	token-limits
o	vesting scripts
o	smoke tests
•	Deployed token on:
o	Fork (dry run)
o	Sepolia
•	Ran fork and Sepolia smoke tests:
o	post
o	launch
o	token-limits
o	vesting
o	swap
•	Tested liquidity addition on fork and Sepolia.
•	Reviewed Hardhat network behavior and Flashbots usage.
•	Verified which wallets must be excluded from max-buy / max-wallet after deployment.
________________________________________
Vesting & Token Distribution
•	Reviewed vesting design (ecosystem, team, advisor).
•	Confirmed beneficiary definitions for vesting releases.
•	Updated:
o	vesting-check-schedule.ts
o	vesting-release.ts
o	vesting-encode.ts
•	Integrated unified guard into vesting flows.
•	Clarified that ecosystem vesting does not require a separate contract.
________________________________________
Tokenomics & Liquidity
•	Reviewed tokenomics structure and potential supply reduction.
•	Added liquidity collector address to config and scripts.
•	Checked LP exclusion rules (fee vs wallet vs buy).
•	Evaluated LP locking vs timelock holding strategy.
•	Reviewed allowance concepts and values.
________________________________________
Website & Documentation (NXK + W3Rooster)
•	Updated security settings:
o	2FA
o	WP admin protection
•	Fixed backup scheduling issues (cron warnings).
•	Rewrote NXK website footer and verified social links.
•	Added Etherscan link to website hero section.
•	Updated homepage sections (FAQ, sliders, project history).
•	Improved SEO:
o	GSC indexing requests
o	JSON-LD improvements
•	Published and distributed:
o	Whitepaper
o	Tokenomics
o	Roadmap
•	Tested responsiveness and lazy loading.
•	Added Tumblr and Threads to social pages.
________________________________________
Socials & Automation
•	Set up and reviewed bots:
o	Telegram
o	Discord
•	Configured auto-post schedules.
•	Published initial W3Rooster posts and verified mobile/social previews.
•	Created NXK articles and scheduled distribution.
•	Managed multi-wallet social and analytics setup.
•	Created Dune Analytics account for future monitoring.
________________________________________
Security Awareness & Operational Readiness
•	Documented response steps for device theft (mobile / desktop).
•	Reviewed Safe security recovery options.
•	Evaluated permissions, approvals, and revocations.
•	Prepared pre-launch checklist for mainnet readiness.
________________________________________
Research, Evaluation & Open Questions
•	Compared fork testing vs localhost testing.
•	Evaluated Tenderly / Foundry simulations.
•	Clarified:
o	Mainnet dry runs
o	Timelock execution flows
o	Post-deployment timelines
•	Compiled remaining tasks before mainnet launch.
________________________________________
Summary
November 2025 focused heavily on security architecture, Safe multisig governance, deployment tooling, vesting logic, and transparency preparation.
No mainnet launch occurred during this period; all work was preparatory, testnet-based, and documentation-driven.

