# Lightning Network Bootstrap Script

This script automates the setup process for Lightning Network nodes, enabling a fast and efficient deployment.

## Usage

1. Ensure you have [Multipass](https://multipass.run/) installed on your system.
2. Launch Multipass instances for each Lightning Network node:
   ```bash
   multipass launch --name alice --cpus 1 --memory 1G 22.04
   multipass launch --name bob --cpus 1 --memory 1G 22.04
   multipass launch --name carol --cpus 1 --memory 1G 22.04
   ```
   Replace `alice`, `bob`, `carol` with the desired names for the nodes.

3. SSH into each Multipass instance and run the script:
   ```bash
   multipass exec alice -- bash -c 'curl -sSL https://raw.githubusercontent.com/mohamedawnallah/bootstrap-lightning-network/main/setup_ln | bash -s $BITCOIN_IP $LN_NODE_ALIAS'
   multipass exec bob -- bash -c 'curl -sSL https://raw.githubusercontent.com/mohamedawnallah/bootstrap-lightning-network/main/setup_ln | bash -s $BITCOIN_IP $LN_NODE_ALIAS'
   multipass exec carol -- bash -c 'curl -sSL https://raw.githubusercontent.com/mohamedawnallah/bootstrap-lightning-network/main/setup_ln | bash -s $BITCOIN_IP $LN_NODE_ALIAS'
   ```
   Initialize the `BITCOIN_IP` env variable with the IP address of your Bitcoin Core node, and
   `LN_NODE_ALIAS` env variable with an optional alias for the Lightning Network node otherwise
   the default `hostname` would be used instead.

## Script Features

- Installs Bitcoin Core (v23.0), Go (go1.22.1), and LND (latest commit in `master` branch).
- Configures Bitcoin and Lightning Network environments (in `regtest` mode).
- Sets up Lightning Network nodes for quick deployment.
- Automatically handles dependencies and environment setup.

## License

This script is licensed under the [MIT License](LICENSE).

## Disclaimer

This script is provided as-is without any warranty. Use at your own risk. The authors and contributors of this script are not liable for any damages or issues arising from its use.
