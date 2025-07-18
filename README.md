# defi-credit-tracker
AI-Powered DeFi Risk Assessment Tool
Problem
In decentralized finance (DeFi), lending platforms on Sei face a significant challenge: assessing the risk of lending to pseudonymous borrowers. Unlike traditional finance, where credit scores and detailed financial histories help evaluate trustworthiness, DeFi relies on blockchain addresses with limited identifiable information. This makes it hard for lenders to gauge the likelihood of repayment, increasing the risk of defaults and reducing confidence in lending protocols.
Solution
Develop an AI-powered risk assessment tool that analyzes on-chain data to generate dynamic risk scores for potential borrowers in Sei’s DeFi lending ecosystem. The AI would examine factors such as:
Transaction history: Frequency, volume, and patterns of activity.

Wallet balances: Total assets, liquidity, and diversity of holdings.

Protocol interactions: Engagement with other DeFi platforms (e.g., borrowing, lending, staking).

Repayment behavior: Historical data on loan repayments (where available).

Using machine learning, the tool would process this data in real-time and assign a risk score to each borrower. Lenders could use these scores to make informed decisions about loan approvals, interest rates, or collateral requirements. The AI could also flag high-risk behaviors, like rapid asset withdrawals or interactions with suspicious contracts.
Benefits
For Lenders: Data-driven insights reduce the chance of defaults and improve lending decisions.

For Borrowers: A fair evaluation based on on-chain activity could unlock better loan terms for users with strong DeFi track records.

For Sei: Boosts trust and adoption of DeFi lending by addressing a critical pain point, leveraging Sei’s fast transaction speeds to process large datasets efficiently.

## Developer Setup

The backend relies on direct queries to Sei's EVM RPC endpoint at
`https://evm-rpc.sei-apis.com`.  Contract addresses and ABIs are read from
environment variables so the scorer can fetch on-chain information about loans,
staking positions, LP tokens and governance events.

Required environment variables:

```
SEI_LENDING_CONTRACT    # Lending protocol contract address
SEI_LENDING_ABI         # Path to JSON ABI for the lending contract
SEI_STAKING_CONTRACT    # Staking contract address
SEI_STAKING_ABI         # Path to staking contract ABI
SEI_LP_TOKEN_CONTRACT   # LP token contract address
SEI_LP_TOKEN_ABI        # Path to LP token ABI
SEI_GOVERNANCE_CONTRACT # Governance contract address
SEI_GOVERNANCE_ABI      # Path to governance contract ABI
SEI_RPC_URL             # Optional custom RPC endpoint (defaults to Sei public RPC)
```

You may use an indexing service if available to avoid scanning the entire chain
when building filters.  Set the above variables accordingly before running the
Python credit scorer.
