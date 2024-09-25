# Fuel-setup-guide


## Introduction

Fuel is a scalable Layer 2 solution for Ethereum that utilizes Optimistic Rollups. This guide will help you set up a validator node for the Fuel network using official resources.

## Prerequisites

Ensure you have the following:

- A server or machine with at least 4 CPU cores, 8 GB of RAM, and 100 GB of SSD storage.
- Ubuntu 20.04 or higher.
- Basic command-line knowledge.

## Step 1: Install Dependencies

First, update your package list and install necessary dependencies:

```bash
sudo apt update
sudo apt install -y curl git
```

## Step 2: Install Rust and Cargo

Install Rust and Cargo, which are required to build the Fuel project:

```bash
curl --proto '=https' --tlsv1.2 -sSf https://sh.rustup.rs | sh
```

Follow the on-screen instructions to complete the installation. After installation, ensure Rust is in your path:

```bash
source $HOME/.cargo/env
```

## Step 3: Clone the Fuel Repository

Clone the official Fuel repository from GitHub:

```bash
git clone https://github.com/FuelLabs/fuel-core.git
cd fuel-core
```

## Step 4: Build the Fuel Node

Build the Fuel node with the following command:

```bash
cargo build --release
```

## Step 5: Configure the Validator Node

Create a configuration file for your validator:

```bash
mkdir ~/.fuel
nano ~/.fuel/config.toml
```

Add the following configuration:

```toml
[network]
chain = "mainnet"  # Use "testnet" for testing

[validator]
enabled = true
```

Save and exit.

## Step 6: Start the Validator Node

Start your validator node using this command:

```bash
./target/release/fuel-core --config ~/.fuel/config.toml
```

## Step 7: Monitor Your Node

You can monitor the logs to ensure your node is running smoothly:

```bash
tail -f ~/.fuel/logs/fuel.log
```

## Step 8: Join the Validator Set

Follow the instructions in the official Fuel documentation to register your node as a validator:

- [Fuel Validator Documentation](https://fuel-labs.github.io/fuel-core/)
