# Yaci DevKit Hackathon Demo

This repository contains examples demonstrating how to use [Yaci DevKit](https://devkit.yaci.xyz) with different Cardano development frameworks:

- **MeshJS** - JavaScript/TypeScript SDK for Cardano
- **Lucid Evolution** - Lightweight Cardano library
- **Cardano Client Lib (CCL)** - Java library for Cardano

## Prerequisites

- **Docker** (for Docker-based installation)
- **Node.js** (v20.8.0 or higher for npm-based installation)
- **Bun** (for running MeshJS and Lucid Evolution examples)
- **JBang** (for running CCL examples)

## Yaci DevKit Installation

### Option 1: Docker Installation (Recommended for local development)

1. Install Yaci DevKit using curl:
   ```bash
   curl --proto '=https' --tlsv1.2 -LsSf https://devkit.yaci.xyz/install.sh | bash
   ```

2. Start the DevKit:
   ```bash
   devkit start
   ```

3. Create and start a default devnet:
   ```bash
   # Inside the Yaci CLI
   create-node -o --start
   ```

4. Access the web interface at http://localhost:5173

### Option 2: NPM Installation (Recommended for CI/CD)

```bash
npm install -g @bloxbean/yaci-devkit
```

Start the DevKit:
```bash
yaci-devkit up --enable-yaci-store
```

### Verify Installation

The DevKit should be accessible on:
- **Node API**: http://localhost:8080
- **Yaci Store (Blockfrost-compatible)**: http://localhost:3001
- **Web Interface**: http://localhost:5173

## Running the Examples

### MeshJS Examples

The MeshJS folder contains examples using Mesh SDK:

1. Navigate to the meshjs folder:
   ```bash
   cd meshjs
   ```

2. Install dependencies:
   ```bash
   bun install
   ```

3. Run examples:
   ```bash
   # Simple payment transaction
   bun run payment.ts

   # Payment splitter with Plutus V3
   bun run payment_splitter_plutusV3.ts
   ```

### Lucid Evolution Examples

The Lucid Evolution folder contains examples using Lucid library:

1. Navigate to the lucid-evo folder:
   ```bash
   cd lucid-evo
   ```

2. Install dependencies:
   ```bash
   bun install
   ```

3. Run examples:
   ```bash
   # Simple payment transaction
   bun run payment.ts

   # Plutus V2 example
   bun run plutus_v2.ts

   # Plutus V3 example
   bun run plutus_v3.ts
   ```

### CCL (Cardano Client Lib) Examples

The CCL folder contains Java examples using JBang:

1. Navigate to the ccl folder:
   ```bash
   cd ccl
   ```

2. Run examples using JBang:
   ```bash
   # Simple transfer example
   jbang SimpleTransfer.java

   # Payment splitter example
   jbang PaymentSplitter.java
   ```

## Project Structure

```
.
├── meshjs/                          # MeshJS examples
│   ├── payment.ts                   # Simple payment example
│   ├── payment_splitter_plutusV3.ts # Plutus V3 smart contract example
│   └── package.json
├── lucid-evo/                       # Lucid Evolution examples
│   ├── payment.ts                   # Simple payment example
│   ├── plutus_v2.ts                 # Plutus V2 example
│   ├── plutus_v3.ts                 # Plutus V3 example
│   └── package.json
├── ccl/                             # Cardano Client Lib examples
│   ├── SimpleTransfer.java          # Simple transfer example
│   ├── PaymentSplitter.java         # Payment splitter example
│   ├── simple-transfer-plutus.json  # Plutus script for simple transfer
│   └── payment-splitter-plutus.json # Plutus script for payment splitter
└── README.md
```

## DevKit Commands

Useful commands when working with Yaci DevKit:

- `devkit start` - Launch containers and CLI
- `devkit stop` - Stop all containers
- `devkit cli` - Run cardano-cli commands
- `devkit ssh` - Connect to the container
- `devkit info` - Display node information
- `devkit version` - Show DevKit version

## Customizing Block Time

You can customize the devnet configuration when creating a node:

```bash
create-node -o --start --block-time 0.5 --slot-length 0.5 --epoch-length 50
```

Parameters:
- `--block-time` - Time between blocks in seconds
- `--slot-length` - Slot duration in seconds
- `--epoch-length` - Number of slots per epoch

## CI/CD Integration

This repository includes a GitHub Actions workflow that automatically runs all examples with Yaci DevKit. The workflow can be manually triggered from the Actions tab.

See [.github/workflows/devkit-ci.yml](.github/workflows/devkit-ci.yml) for the complete CI configuration.

## Resources

- [Yaci DevKit Documentation](https://devkit.yaci.xyz)
- [Yaci DevKit Getting Started](https://devkit.yaci.xyz/getting-started/docker)
- [Yaci DevKit CI Integration](https://devkit.yaci.xyz/ci-integration)
- [MeshJS Documentation](https://meshjs.dev)
- [Lucid Evolution](https://github.com/Anastasia-Labs/lucid-evolution)
- [Cardano Client Lib](https://github.com/bloxbean/cardano-client-lib)

## Troubleshooting

### Port conflicts
If you encounter port conflicts, ensure ports 3001, 8080, and 5173 are available.

### Docker not running
Make sure Docker is installed and running before executing `devkit start`.

### Node version issues
Ensure you're using Node.js v20.8.0 or higher for npm-based installation.

## License

ISC
