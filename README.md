# 🛡️ VAULT (VLT) — Core C++ Daemon, CLI & RPC Server

[![Website](https://img.shields.io/badge/Website-vaultapp.space-00f2fe?style=for-the-badge&logo=googlechrome&logoColor=white)](https://vaultapp.space)
[![X / Twitter](https://img.shields.io/badge/X%2F%20Twitter-@VaultMe-1DA1F2?style=for-the-badge&logo=x&logoColor=white)](https://x.com/VaultMe)
[![Telegram](https://img.shields.io/badge/Telegram-@Vault__Space-26A5E4?style=for-the-badge&logo=telegram&logoColor=white)](https://t.me/Vault_Space)
[![Discord](https://img.shields.io/badge/Discord-Join_Community-5865F2?style=for-the-badge&logo=discord&logoColor=white)](https://discord.gg/VZyvT)
[![Blockchain Explorer](https://img.shields.io/badge/Explorer-8.229.216.134%3A3000-7f00ff?style=for-the-badge&logo=express&logoColor=white)](http://8.229.216.134:3000)
[![Desktop GUI Wallets](https://img.shields.io/badge/GUI_Wallets-vault--wallets-10b981?style=for-the-badge&logo=github&logoColor=white)](https://github.com/vaultapp-space/vault-wallets)
[![License](https://img.shields.io/badge/License-BSD_3_Clause-ff6b6b?style=for-the-badge&logo=open-source-initiative&logoColor=white)](LICENSE)

Welcome to the official repository for the **VAULT (VLT)** core C++ cryptocurrency implementation — including the full node daemon (`vaultd`), command-line wallet (`vault-wallet-cli`), and JSON-RPC server (`vault-wallet-rpc`).

VAULT is an untraceable, privacy-centric digital currency built on CryptoNote and Ring Confidential Transactions (RingCT).

---

## 🌐 Official Channels & Social Links

- **🌐 Website**: [https://vaultapp.space](https://vaultapp.space)
- **𝕏 / Twitter**: [@VaultMe](https://x.com/VaultMe)
- **💬 Telegram Community**: [@Vault_Space](https://t.me/Vault_Space)
- **👾 Discord Server**: [Join Discord Community](https://discord.gg/VZyvT)
- **🔍 Block Explorer**: [http://8.229.216.134:3000](http://8.229.216.134:3000)
- **💼 Desktop Core GUI Wallets**: [https://github.com/vaultapp-space/vault-wallets](https://github.com/vaultapp-space/vault-wallets)

---

## 🌟 About VAULT (VLT)

VAULT (`VLT`) is designed for untraceable, borderless, instant private payments. Every transaction on the VAULT network is cryptographically protected by default:

- **🔒 Ring Confidential Transactions (RingCT)**: Conceals transaction amounts and inputs/outputs.
- **🛡️ Stealth Addresses**: Generates dynamic, one-time destination keys (`d5...`) for total receiver anonymity.
- **⚡ Fast 60-Second Blocks**: High transaction throughput and low latency block confirmations.
- **⛏️ CPU-Friendly Mining**: Decentralized consensus designed for ordinary CPU hardware.

---

## ⚙️ Core Technical Specifications

| Parameter | Value | Description |
| :--- | :--- | :--- |
| **Coin Name** | **VAULT** | Privacy Cryptocurrency |
| **Ticker** | `VLT` | Symbol |
| **Address Prefix** | `d5` | Mainnet standard address prefix |
| **Target Block Time** | `60 seconds` | Block generation frequency |
| **Atomic Unit Scale** | `10^12` | 1 VLT = 1,000,000,000,000 atomic units |
| **P2P Port** | `29080` | Peer-to-peer network protocol |
| **Daemon RPC Port** | `29081` | Core node JSON-RPC interface |
| **ZMQ Port** | `29082` | ZeroMQ pub/sub message queue |
| **Wallet RPC Port** | `29083` | Wallet RPC server port |
| **Explorer Web Port** | `3000` | Web block explorer |
| **Seed Node Host** | `8.229.216.134:29081` | Official seed & RPC node |

---

## 🛠️ Compiling VAULT from Source

### 🍎 1. macOS (Apple Silicon ARM64 & Intel)

#### Dependencies (Homebrew)
```bash
brew update
brew install cmake boost openssl@3 unbound zeromq hidapi libsodium libusb ccache pkg-config
```

#### Build Instructions
```bash
git clone https://github.com/vaultapp-space/VAULT.git
cd VAULT
mkdir -p build/release && cd build/release
cmake -D CMAKE_BUILD_TYPE=Release -D MANUAL_SUBMODULES=1 ../..
make -j$(sysctl -n hw.ncpu)
```

The compiled binaries will be located in `bin/`:
- `vaultd` (Daemon executable)
- `vault-wallet-cli` (Command-line wallet)
- `vault-wallet-rpc` (Wallet RPC server)

---

### 🐧 2. Ubuntu / Debian Linux

#### Dependencies
```bash
sudo apt update
sudo apt install -y build-essential cmake pkg-config libboost-all-dev libssl-dev libunbound-dev libzeromq3-dev libsodium-dev libhidapi-dev libusb-1.0-0-dev git
```

#### Build Instructions
```bash
git clone https://github.com/vaultapp-space/VAULT.git
cd VAULT
mkdir -p build/release && cd build/release
cmake -D CMAKE_BUILD_TYPE=Release -D MANUAL_SUBMODULES=1 ../..
make -j$(nproc)
```

---

## 🚀 Running `vaultd` Daemon

### Start Local Node Daemon
```bash
./bin/vaultd --data-dir ~/.vault-blockchain --rpc-bind-ip 127.0.0.1 --rpc-bind-port 29081 --non-interactive --log-level 1
```

### Common Command Line Options
- `--data-dir <path>`: Specify local directory for LMDB blockchain database.
- `--rpc-bind-ip <ip>`: Bind IP address for local JSON-RPC server (`127.0.0.1`).
- `--rpc-bind-port <port>`: Port for JSON-RPC server (`29081`).
- `--offline`: Run daemon in standalone mode without P2P network handshakes.
- `--start-mining <d5...address>`: Enable local CPU solo mining to a recipient wallet address.
- `--mining-threads <count>`: Set CPU thread count for local mining.

---

## 💻 Running Command-Line Wallet (`vault-wallet-cli`)

### Create a New Wallet
```bash
./bin/vault-wallet-cli --daemon-address 127.0.0.1:29081 --generate-new-wallet my_vault_wallet
```

### Restore Wallet from 25-Word Mnemonic Seed
```bash
./bin/vault-wallet-cli --daemon-address 8.229.216.134:29081 --restore-deterministic-wallet
```

---

## 🖥️ Desktop GUI Wallet

For a modern, pure pitch-black graphical desktop experience on **macOS** and **Windows**, download the pre-built desktop application:

👉 **[VAULT Desktop GUI Wallet Repository](https://github.com/vaultapp-space/vault-wallets)**
👉 **[Download Latest Releases (v1.1.0)](https://github.com/vaultapp-space/vault-wallets/releases)**

---

## 📄 License

The VAULT Project is licensed under the **BSD 3-Clause License**. See [LICENSE](LICENSE) for details.
