# Raegis RWA Dashboard

The official web interface for the **Raegis RWA Protocol**. Built with Next.js, this dashboard provides a seamless UI for administrators to mint compliant Real-World Assets and for investors to manage their portfolios.

## Prerequisites

- [Node.js](https://nodejs.org/en/) (v18+)
- [Freighter Wallet](https://www.freighter.app/) Browser Extension

## Local Setup

1. Clone the repository and install dependencies:
```bash
   npm install
```
2. Run the development server:
```bash
   npm run dev
```
3. Open http://localhost:3000 in your browser.
## Contribution Guidelines
We welcome frontend contributions! Check [CONTRIBUTING.md](CONTRIBUTING.md) for our branching strategies and Tailwind styling rules. Look for `// TODO:` comments in the codebase for easy wins.

## Contributing

We welcome frontend contributions! Please read our [Contributing Guide](CONTRIBUTING.md) before submitting a pull request.

Key resources for contributors:

- [Evaluation Readiness Dashboard](docs/evaluation-readiness.md) — Central summary page for testing standards, CI workflow, PR evidence, acceptance criteria mapping, self-review, and payment guidance
- [Contributing Guide](CONTRIBUTING.md) — Branch naming, component rules, PR evidence checklist, and review process
- [Low-Effort PR Examples](docs/low-effort-pr-examples.md) — Examples of superficial, under-tested, or unsafe PRs that will fail evaluation
- [Evaluation-Readiness Index](docs/evaluation-readiness-index.md) — Central page linking every requirement for GrantFox evaluation: payment expectations, testing standards, CI guidance, acceptance criteria audit, self-assessment, and reviewer checklist
- [Issue Approval Readiness Checklist](docs/issue-approval-readiness-checklist.md) — Pre-evaluation checklist for contributors and reviewers to verify implementation completeness, testing, CI, acceptance criteria, documentation, and known limitations before GrantFox evaluation
- [PR Evidence Checklist](docs/pr-evidence-checklist.md) — Detailed requirements for pull request evidence and documentation
- [Test-First Contribution Guide](docs/test-first-contribution-guide.md) — How to write tests before code, with area-specific patterns and examples
- [Aegis Dashboard Minimum Testing Standard](docs/testing-standard.md) — Minimum test coverage for admin workflows, investor views, compliance screens, asset registration, minting, wallet connection, and diagnostics
- [Aegis SDK Testing Standard](docs/sdk-testing-standard.md) — Minimum unit, integration, and negative-path test coverage for compliance, KYC, RWA metadata, investor reads, admin actions, and transaction receipts
- [Architecture Overview](docs/architecture.md) — Component hierarchy and state management
- [Frontend Developer Guide](docs/frontend-guide.md) — Styling conventions and page creation
- [Compliance Reviewer Workflow](docs/compliance-reviewer-workflow.md) — Guide for compliance operators reviewing investor eligibility
- [Investor Transfer Request Flow](docs/investor-transfer-request-flow.md) — Request-validation edge cases (address, self-transfer, amount, precision) and RPC-failure handling for the transfer modal
- [RWA Asset Minting Workflow](docs/rwa-asset-minting-workflow.md) — Admin mint: asset selector, compliance pre-check, review, Freighter signing, receipt (Issue #6)
- [Compliance-Safe Wording Guidance](docs/compliance-safe-wording.md) — Canonical disclaimer text, typed helper, and reviewer checklist for compliance-facing copy
- [RWA Asset Lifecycle Status](docs/asset-lifecycle-status.md) — Lifecycle state machine, transition validation, and status UI for already-minted RWA assets
- [Bulk Compliance Review](docs/bulk-compliance-review.md) — Bulk compliance review table with action confirmation modal
- [Compliance Status Panel](docs/compliance-status-panel.md) — Address-level compliance status for investor and admin views (Issue #175)
- [Transaction Review Modal](docs/transaction-review-modal.md) — Pre-signature review modal, operation summary mapper, and risk notes (Issue #177)
- [Admin Action Receipts](docs/admin-action-receipts.md) — Privileged action status, target, hash, explorer link, and next-step guidance (Issue #179)
- [Environment Mismatch Blocking Screen](docs/environment-mismatch-blocking.md) — Full-page blocking screen when the wallet network does not match the dashboard target network
- [Wallet Network Guard](docs/wallet-network-guard.md) — Per-action network guard: live Freighter network detection, block-versus-warn policy, and network assumptions (Issue #180)
- [Investor Onboarding Eligibility](docs/investor-onboarding-eligibility.md) — Investor onboarding eligibility page, evaluation precedence, and SDK mapping
- [Performance Budget Review](docs/performance-budget-review.md) — Typed budget threshold evaluation, edge cases, and reviewer checklist

> **Note:** All pull requests must follow the [PR Evidence Checklist](docs/pr-evidence-checklist.md) and be audited against the [Evaluation Readiness Dashboard](docs/evaluation-readiness.md) before requesting review.

The transactions page also includes a contributor-ready fixture gallery for transaction review, progress, and receipt states. See [docs/transaction-components.md](docs/transaction-components.md) for the shared component contract, fixture expectations, and compliance-safe wording guidance.

## Transfer Restriction Explainer
Investor-facing transfer flows now include a reusable explainer for transfer restrictions. The logic lives in [src/lib/eligibility.ts](src/lib/eligibility.ts) and the UI is surfaced in the investor portfolio and transfer modal. See [docs/investor-transfer-eligibility.md](docs/investor-transfer-eligibility.md) for the typed state model, edge cases, and compliance-safe wording guidance.

## Route Access
Role-aware route guards protect admin, issuer, investor, and read-only sections. See `docs/route-access.md` for route mapping, guard states, SDK assumptions, and mock wallet fixtures.
