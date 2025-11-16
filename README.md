# Launchpad Service (DeMiPad – Permissioned Launchpad)

**Launchpad (DeMiPad)** is a permissioned asset launch platform developed by Demiourgos.Holdings on the Ouronet network. It allows administrators to create, manage, and operate secure token sales while enforcing limits, fees, and governance rules.

- **Business Audience**: Investors, project managers, and administrators participating in token launches.
- **Repository**: [GitHub Launchpad](https://github.com/ouronetwork/Launchpad)
- **Documentation**: [Permissioned Launchpad (GitBook)](https://demiourgos-holdings-tm.gitbook.io/kadena/ouronet-services/demipad-permissioned-launchpad)
- **Smart Contract Reference**: [DemiPact Smart Contracts](https://github.com/AncientHodler/DemiPact/tree/main/DemiourgosSC)

---

## Business Overview

Launchpad provides:

- **Controlled Asset Sales**: Only authorized administrators can create, modify, and launch assets.
- **Rule-Based Automation**: Custom rules for pricing, phased intervals, and purchase limits.
- **Secure Token Management**: All transactions are enforced via Kadena smart contracts.
- **Transparency and Auditability**: Full visibility into sales, allocations, and participant accounts.
- **Sandbox Testing**: Clients can explore functionality in a preconfigured environment before going live.

---

## Technical Overview (Client Perspective)

The repository contains Pact smart contracts (`.pact`) and REPL scripts (`.repl`) for Launchpad. Clients can use the Kadena REPL sandbox to simulate launches off-chain without touching production assets.

**Sandbox Environment**

- Based on [kadena_repl_sandbox](https://github.com/CryptoPascal31/kadena_repl_sandbox)
- Preloaded with:
  - Standard Kadena modules and utilities
  - Coin contract and `fungible-v2` interfaces
  - Marmalade contracts for token management
  - Pre-funded test accounts: `alice`, `bob`, `carol`, `dave` (1000 KDA each)

---

## Running the Sandbox

1) **Install Pact**

Download and install the Pact CLI from [Kadena Releases](https://github.com/kadena-io/pact/releases).

2) **Clone the Launchpad repository**

```bash
git clone https://github.com/ouronetwork/Launchpad.git
cd Launchpad
```

3) **Create a REPL file**

Create a file named `launchpad_test.repl` that loads the sandbox environment:

```lisp
(env-data {})
(load "kda-env/init.repl")
```

4) **Launch the REPL**

```bash
pact launchpad_test.repl
```

You should see messages confirming the sandbox environment is initialized and the pre-funded accounts are ready.

### Test Contracts

You can execute `.pact` scripts and REPL commands to simulate:

- Creating assets
- Funding accounts
- Executing token sales
- Checking balances and sale rules

No real funds are used; this is a safe sandbox for testing and demonstration.

---

## Client Use Cases

- **Demonstration**: Explore how asset launches work before committing to real operations.
- **Validation**: Ensure token rules and allocation logic match business requirements.
- **Training**: Onboard team members to the Launchpad workflow in a safe, isolated environment.

---

## Support & Resources

- **Official Documentation**: [Permissioned Launchpad (GitBook)](https://demiourgos-holdings-tm.gitbook.io/kadena/ouronet-services/demipad-permissioned-launchpad)
- **Smart Contract Reference**: [DemiPact (GitHub)](https://github.com/AncientHodler/DemiPact/tree/main/DemiourgosSC)
- **REPL Sandbox**: [kadena_repl_sandbox (GitHub)](https://github.com/CryptoPascal31/kadena_repl_sandbox)

---

Launchpad enables secure, rule-driven asset sales with transparency. Clients can experiment and validate operations in the sandbox before any production deployment.


