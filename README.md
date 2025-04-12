🧰 Prerequisites
Before getting started, make sure you have the following:
A Linux-based system (Ubuntu 20.04+ or WSL on Windows)
A Backpack wallet (or another Eclipse-compatible wallet) Download
0.005+ ETH on the Eclipse network
Getting Started
Prepare Environment
image

sudo apt update && sudo apt upgrade -y
sudo apt install curl nano build-essential -y
Build Screen from Source
sudo apt install autoconf make gcc libutempter-dev libpam0g-dev libncurses5-dev -y
curl -O https://ftp.gnu.org/gnu/screen/screen-4.9.1.tar.gz
tar -xzf screen-4.9.1.tar.gz
cd screen-4.9.1
./configure
make
sudo make install
Check screen version
screen --version 
image

Install RUST
curl --proto '=https' --tlsv1.2 -sSf https://sh.rustup.rs | sh
image

Press 1 to proceed

source $HOME/.cargo/env
Install Solana CLI
curl --proto '=https' --tlsv1.2 -sSfL https://solana-install.solana.workers.dev | bash 
image

After Installation, reload terminal
source $HOME/.bashrc
image

Check Version
solana --version
if using VPS, and Solana not found, REBOOT

reboot
Configue RPC for Eclipse
This connects CLI to the Eclipse mainnet.
solana config set --url https://mainnetbeta-rpc.eclipse.xyz/ 
image

Wallet Setup (Solana Keypair)
Create New Keypair
solana-keygen new
Press ENTER and save the passphrase

Exporting PrivateKey from ID.json
cat ~/.config/solana/id.json
Copy the output (a list of numbers) and import it into Backpack Wallet under “Private Key”.
Fund the wallet with 0.005+ ETH on Eclipse to activate mining.
Install Bitz CLI
This compiles and installs the Bitz miner directly from source.
cargo install bitz
image

 Start Mining Bitz by opening Screen
screen -S bitzminer
Start Miner
bitz collect
Using Multiple core
bitz collect --cores 4
To keep it running in the background:
Detach screen: Ctrl + A + D
Reattach screen: ```screen -r bitzminer``
List screens: screen -ls
Stop miner: Ctrl + C inside screen
Kill screen: screen -XS bitzminer quit
I used 4 cores here (will adjsut appropriately according to my SPEC) image

Claim Mined tokens
bitz claim
Check Wallet status
bitz account

✅ Final Notes
Always keep a backup of your id.json file and mnemonic
Bitz mining only works if your wallet is funded with ETH on Eclipse
You can run this setup on basic VPS (e.g., 1 vCPU, 1GB RAM)
DONE!
