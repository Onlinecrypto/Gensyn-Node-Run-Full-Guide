RL Swarm Node - Full Setup Guide (PC | VPS | Mac)

tmux new-session -s rlswarm

# Then inside tmux, run your node
docker compose up

# To detach from tmux session:
Ctrl + B, then press D

# To reattach later:
tmux attach-session -t rlswarm

> Official Docs: Gensyn RL Swarm GitHub
Dashboard (Check Points): https://dashboard.gensyn.ai/




---

1⃣ Install Dependencies

✅ For WSL / Linux / VPS:

sudo apt update && sudo apt upgrade -y

sudo apt install -y curl git wget nano tmux htop nvme-cli lz4 jq make gcc clang build-essential autoconf automake pkg-config libssl-dev libleveldb-dev libgbm1 bsdmainutils ncdu unzip tar

✅ For MacOS:

Install Homebrew (if not already):

/bin/bash -c "$(curl -fsSL https://raw.githubusercontent.com/Homebrew/install/HEAD/install.sh)"

Then install required packages:

brew install cmake protobuf rust python@3.10


---

2⃣ Clone RL Swarm Repo

git clone https://github.com/gensyn-ai/rl-swarm.git

cd rl-swarm


---

3⃣ Install Rust (If not installed)

curl --proto '=https' --tlsv1.2 -sSf https://sh.rustup.rs | sh

source $HOME/.cargo/env


---

4⃣ Run the Node

Option 1: Run with Docker

Install Docker (if not installed):

curl -fsSL https://get.docker.com | sh

Then run:

docker compose up

> Note: First time it will download and build everything (can take some time).




---

Option 2: Run Without Docker (Using Cargo)

cargo build --release

cargo run --release


---

5⃣ Check If It's Working

Once the node is running, you should see logs in the terminal with progress.
To monitor your stats and points, go to:

> https://dashboard.gensyn.ai/



Log in with the wallet you used during setup.


---

6⃣ (Optional) Run Node in Background (Linux/VPS)

Use tmux to keep your node running after disconnecting SSH:

tmux new-session -s rlswarm

# Then inside tmux, run your node
docker compose up

# To detach from tmux session:
Ctrl + B, then press D

# To reattach later:
tmux attach-session -t rlswarm


---

7⃣ Tips

Make sure your internet is stable.

Keep the terminal open or use tmux for background running.

Restart the node if it crashes occasionally.



---

Support

If you're stuck, you can refer to official GitHub issues or join the Gensyn community on Discord.

