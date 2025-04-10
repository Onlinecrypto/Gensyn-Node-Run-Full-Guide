# RL Swarm Node Run Full Guide (PC, VPS & Mac)

## Official Resources

- **Docs:** [https://github.com/gensyn-ai/rl-swarm?tab=readme-ov-file](https://github.com/gensyn-ai/rl-swarm?tab=readme-ov-file)
- **Dashboard (check your points):** [https://dashboard.gensyn.ai/](https://dashboard.gensyn.ai/)

---

## 1 Dependencies for Windows, Linux (WSL/VPS) & Mac

### For WSL or VPS:

```bash
sudo apt update && sudo apt upgrade -y
sudo apt install -y curl git wget nano tmux htop nvme-cli lz4 jq make gcc clang build-essential autoconf automake pkg-config libssl-dev libleveldb-dev libgbm1 bsdmainutils ncdu unzip tar
```

### For Mac:

```bash
brew install git curl wget nano tmux htop jq make gcc autoconf automake pkg-config openssl leveldb lz4 coreutils
```

---

## 2 Install Python, Node.js, Yarn, NPM, Pip & Dev Tools

### For WSL or VPS:

```bash
sudo apt-get install python3 python3-pip python3-venv python3-dev -y
```

```bash
sudo apt-get update && curl -fsSL https://deb.nodesource.com/setup_22.x | sudo -E bash -
sudo apt-get install -y nodejs
node -v && npm -v
sudo npm install -g yarn && yarn -v
```

```bash
sudo apt install -y python3 python3-pip
python3 --version && pip3 --version
```

```bash
sudo apt install python3-dev python3-venv build-essential -y
```

```bash
sudo apt-get update && sudo apt-get install -y curl gnupg apt-transport-https
curl -sS https://dl.yarnpkg.com/debian/pubkey.gpg | sudo apt-key add -
echo "deb https://dl.yarnpkg.com/debian/ stable main" | sudo tee /etc/apt/sources.list.d/yarn.list
sudo apt-get update && sudo apt-get install -y yarn
yarn --version
```

### For Mac:

```bash
brew install python3 node yarn
```

---

## 3 Hugging Face Access Token (Optional)

Not needed.

---

## 4 Download RL Swarm Files

```bash
git clone https://github.com/gensyn-ai/rl-swarm/
cd rl-swarm
```

### VPS ONLY:

```bash
apt install screen -y
screen -S rlswarm
```

---

## 5 Install and Run RL Swarm

```bash
python3 -m venv .venv
source .venv/bin/activate
./run_rl_swarm.sh
```

- Type `Y` and press Enter
- Wait until it says: **"waiting for UserData.json to be created"**
- Then open browser and go to: [http://localhost:3000/](http://localhost:3000/) and login via Google

### When prompted:

> Would you like to push models you train in the RL swarm to the Hugging Face Hub? [y/N]  
Choose `N`

- Note down your Username.

---

## VPS: Open Another Window to Login to Localhost

### 1 Allow Port 3000

```bash
sudo apt install ufw -y
sudo ufw allow 3000/tcp
sudo ufw enable
```

### 2 Install Cloudflared

```bash
wget -q https://github.com/cloudflare/cloudflared/releases/latest/download/cloudflared-linux-amd64.deb
sudo dpkg -i cloudflared-linux-amd64.deb
cloudflared --version
```

### 3 Create Tunnel

Make sure your node is running at port `3000`, then:

```bash
cloudflared tunnel --url http://localhost:3000
```

Use the generated URL in your browser to access the node and log in.

To detach screen:

```bash
CTRL + A + D
```

To re-open it:

```bash
screen -r rlswarm
```

---

## Backup: Save `swarm.pem` File to Local Machine

### From VPS to WSL (Linux):

```bash
scp USERNAME@YOUR_IP:~/rl-swarm/swarm.pem ~/swarm.pem
```

### From VPS to Windows Desktop:

**If username has no spaces:**

```bash
scp USERNAME@YOUR_IP:~/rl-swarm/swarm.pem C:\Users\YourUsername\Desktop\
```

**If username has spaces:**

```bash
scp USERNAME@YOUR_IP:~/rl-swarm/swarm.pem "/mnt/c/Users/Your Username/Desktop/"
```

### From WSL to Desktop:

```bash
cp ~/rl-swarm/swarm.pem /mnt/c/Users/YourUsername/Desktop/
```

**If username has spaces:**

```bash
cp ~/rl-swarm/swarm.pem "/mnt/c/Users/Your Username/Desktop/"
```

### From Mac to Desktop:

```bash
cp ~/rl-swarm/swarm.pem ~/Desktop/
```

### To Check Windows Username:

```powershell
echo %USERNAME%
```

---

## For Daily Usage (Next Day Start)

```bash
cd rl-swarm
python3 -m venv .venv
source .venv/bin/activate
./run_rl_swarm.sh
```

---

## Delete Node Folder

```bash
rm -rf ~/rl-swarm
```

---

## Backup API Key and User Data

```bash
cat ~/rl-swarm/modal-login/temp-data/userApiKey.json
cat ~/rl-swarm/modal-login/temp-data/userData.json
```
