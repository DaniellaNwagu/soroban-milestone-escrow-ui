# Soroban Milestone Escrow UI

A Next.js frontend for a milestone-based escrow application built on Stellar and Soroban. The project provides interfaces for creating escrow jobs, managing milestones, connecting Stellar wallets, and interacting with escrow workflows.

**Network:** Stellar Testnet

> **Development status:** Some dashboard actions are still awaiting contract integration. This project should be treated as a testnet development application, not as production-ready financial software.

## Features

- **Escrow creation:** Create jobs and configure milestone details.
- **Job dashboard:** View escrow jobs, milestone statuses, and available actions.
- **Stellar wallet integration:** Connect supported wallets and sign transactions using the Stellar Wallets Kit.
- **Transaction feedback:** Display notifications and handle wallet and transaction states.
- **Dispute management:** Access dispute-related interfaces and arbitration workflows.
- **Refund and claim interfaces:** Access client refund and freelancer claim functionality where supported.
- **Administrative controls:** Manage whitelisted tokens and access contract administration interfaces.
- **Responsive interface:** Reusable UI components with accessibility and responsive-design tests.

Not every interface is necessarily connected to a working on-chain transaction. Check the implementation and tests for the current status of each workflow.

## Technology Stack

- Next.js 16
- React 19
- TypeScript
- Tailwind CSS 4
- Stellar SDK
- Stellar Wallets Kit
- Vitest
- React Testing Library

## Application Routes

| Route | Description |
|---|---|
| `/` | Landing page |
| `/create` | Create an escrow job with milestones |
| `/dashboard` | View escrow jobs and milestone actions |
| `/admin` | Administrative interface, including token management |

Access to administrative operations depends on the permissions enforced by the application and smart contract.

## Deployed Contract

| Setting | Value |
|---|---|
| Network | Stellar Testnet |
| Contract ID | `CDD5WKK3WT3QVKXMXTJNDIXE4T73FK6GGXDSD6UTJAH6YYZU52SQ4MUH` |

[View the contract on Stellar Expert](https://stellar.expert/explorer/testnet/contract/CDD5WKK3WT3QVKXMXTJNDIXE4T73FK6GGXDSD6UTJAH6YYZU52SQ4MUH)

## Prerequisites

- Node.js 24
- npm
- Git
- A compatible Stellar wallet for wallet-dependent workflows
- Access to the companion backend for features that require backend APIs

Use Stellar Testnet accounts and test assets when developing and testing the application.

## Getting Started

### 1. Clone the repository

```bash
git clone https://github.com/DaniellaNwagu/soroban-milestone-escrow-ui.git
cd soroban-milestone-escrow-ui
```

### 2. Install dependencies

```bash
npm ci
```

### 3. Configure environment variables

Copy the example environment file.

**macOS/Linux**

```bash
cp .env.local.example .env.local
```

**Windows PowerShell**

```powershell
Copy-Item .env.local.example .env.local
```

Configure `.env.local`:

```dotenv
NEXT_PUBLIC_CONTRACT_ID=CDD5WKK3WT3QVKXMXTJNDIXE4T73FK6GGXDSD6UTJAH6YYZU52SQ4MUH
NEXT_PUBLIC_BACKEND_URL=http://localhost:3001
NEXT_PUBLIC_SOROBAN_RPC_URL=https://soroban-testnet.stellar.org
NEXT_PUBLIC_SOROBAN_NETWORK_PASSPHRASE=Test SDF Network ; September 2015
```

These values match the variables documented in `.env.local.example`. Update the backend URL if your backend runs at a different address.

**Security:** Variables prefixed with `NEXT_PUBLIC_` are exposed to the browser. Never put wallet secret keys, seed phrases, or private credentials in these variables.

### 4. Run the development server

```bash
npm run dev
```

Open [http://localhost:3000](http://localhost:3000).

Features requiring backend access will also need the companion backend configured and running.

## Available Scripts

| Command | Purpose |
|---|---|
| `npm run dev` | Start the development server |
| `npm run build` | Build the application for production |
| `npm run start` | Start the production server |
| `npm run lint` | Run ESLint |
| `npm run type-check` | Run the TypeScript type checker |
| `npm run test` | Run the Vitest test suite |

Run the checks before submitting changes:

```bash
npm run lint
npm run type-check
npm run test
npm run build
```

## Testing

The project uses Vitest and React Testing Library. The existing test suite includes coverage for wallet behavior, milestone components, dashboard states, accessibility, responsive layouts, and transaction feedback.

When making changes:

- Add tests for new behavior.
- Cover both successful operations and relevant failure cases.
- Mock wallet signing and network interactions where appropriate.
- Avoid requiring real funds or private wallet credentials in automated tests.
- Verify that UI state reflects the result of contract operations.

## Related Repositories

- [Soroban Escrow Contract](https://github.com/Goldii-locks/escrow-contract)
- [Escrow Backend](https://github.com/Goldii-locks/escrow-backend)

The frontend, backend, and contract must use compatible interfaces, transaction arguments, and network configuration.

## Contributing

Contributions that improve contract integration, wallet reliability, testing, accessibility, and documentation are welcome.

1. Check existing issues and recent pull requests before starting work.
2. Discuss substantial changes in an issue before implementation.
3. Keep pull requests focused and provide clear reproduction steps.
4. Add or update tests for modified behavior.
5. Run the relevant lint, type-check, test, and build commands.
6. Document new environment variables or setup requirements.
7. Describe your changes and verification steps in the pull request.

## Security Disclaimer

This application is configured for Stellar Testnet. Its presence of escrow, refund, dispute, and administrative interfaces does not guarantee that every workflow is fully implemented or secure for production.

Verify the contract behavior and transaction details before signing. Never share your wallet secret key or recovery phrase.
