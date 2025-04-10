# RL Swarm Node Run Full Guide (PC, VPS & Mac)

### Offical Docs:  
[https://github.com/gensyn-ai/rl-swarm](https://github.com/gensyn-ai/rl-swarm?tab=readme-ov-file)

### Dashboard (Check your Points):  
[https://dashboard.gensyn.ai/](https://dashboard.gensyn.ai/)

---

## 1ï¸âƒ£ Install Dependencies for Windows / Linux / VPS / Mac

### For WSL / VPS (Ubuntu/Debian based)

```bash
sudo apt update && sudo apt upgrade -y

sudo apt install -y curl git wget nano tmux htop nvme-cli lz4 jq make gcc clang build-essential autoconf automake pkg-config libssl-dev libleveldb-dev libgbm1 bsdmainutils ncdu unzip tar
```

---

## 2ï¸âƒ£ Clone the Repo & Install Rust

```bash
git clone https://github.com/gensyn-ai/rl-swarm.git
cd rl-swarm

curl --proto '=https' --tlsv1.2 -sSf https://sh.rustup.rs | sh
source $HOME/.cargo/env
```

---

## 3ï¸âƒ£ Run the Node

### Option 1: Run with Docker

Install Docker:

```bash
curl -fsSL https://get.docker.com | sh
```

Run the node:

```bash
docker compose up
```

**Note:** First time it will download and build everything (can take some time).

---

### Option 2: Run Without Docker (Using Cargo)

```bash
cargo build --release
cargo run --release
```

---

## 4ï¸âƒ£ Check if it's Working

Open your browser and go to:

```
http://localhost:3000
```

---

## 5ï¸âƒ£ Open Another Window to Tunnel VPS â†’ Localhost

### Step 1: Install UFW and Allow Port

```bash
sudo apt install ufw -y
sudo ufw allow 3000/tcp
```

### Step 2: Enable UFW

```bash
sudo ufw enable
```

### Step 3: Install Cloudflared

```bash
wget -q https://github.com/cloudflare/cloudflared/releases/latest/download/cloudflared-linux-amd64.deb
sudo dpkg -i cloudflared-linux-amd64.deb
cloudflared --version
```

### Step 4: Run Tunnel Command

```bash
cloudflared tunnel --url http://localhost:3000
```

---

## 6ï¸âƒ£ Tips

- Make sure your node is running on port **3000** before running Cloudflared.
- Use `tmux` to keep your node running after disconnecting SSH.

---

## âœ… You're All Set!

Now monitor your progress at:  
[https://dashboard.gensyn.ai/]
