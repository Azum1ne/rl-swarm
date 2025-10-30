# 🧠 RL-Swarm (Private Setup)
  
#### Thanks to **arcxteam** & **gasoline** for the base setup references.

---

## ⚙️ Installation Setup

### 1️⃣ Update System Packages
```bash
apt update && apt upgrade -y && \
apt install screen curl ufw nload tree iptables git wget lz4 jq make gcc nano automake autoconf \
htop tmux libgbm1 protobuf-compiler python3 python3-pip python3-venv python3-dev python3-setuptools \
tar clang nethogs ncdu unzip build-essential pkg-config libssl-dev libleveldb-dev \
speedtest-cli ca-certificates libffi-dev libsqlite3-dev -y
```

---

### 2️⃣ Install Node.js, NPM, Yarn, and PM2
```bash
source <(wget -qO- https://raw.githubusercontent.com/arcxteam/w-ai-wombo/main/nodejs.sh)
```

---

### 3️⃣ Install Cloudflared Tunnel
```bash
wget https://github.com/cloudflare/cloudflared/releases/latest/download/cloudflared-linux-amd64.deb
dpkg -i cloudflared-linux-amd64.deb || apt-get install -f -y
```

---

### 4️⃣ Clone Repository & Replace `run_rl_swarm.sh`
```bash
git clone https://github.com/arcxteam/rl-swarm.git && \
cd rl-swarm && \
rm -f run_rl_swarm.sh && \
wget https://raw.githubusercontent.com/Azum1ne/rl-swarm/main/run_rl_swarm.sh -O run_rl_swarm.sh && \
chmod +x run_rl_swarm.sh && \
git clone https://github.com/gasoline2255/genrl && \
echo "✅ RL-Swarm ready with run_rl_swarm.sh from Gensyn-Testnet"
```

---

### 5️⃣ Create Screen Session
```bash
screen -S gensyn
```

---

### 6️⃣ Set Up Python Virtual Environment
```bash
python3 -m venv .venv
source .venv/bin/activate
# If that doesn't work, try:
. .venv/bin/activate

# Install vLLM
pip install vllm
```

---

### 7️⃣ Run RL Swarm
```bash
./run_rl_swarm.sh
```

---

## 🐳 Docker (CPU Only)
```bash
docker compose run --rm --build -Pit --user 0:0 swarm-cpu
```

---

## 🔑 Login (Tunnel Access)
Once `run_rl_swarm.sh` is running, open the tunnel for login:
```bash
cloudflared tunnel --url http://localhost:3000
```
Then open the provided URL in your browser to complete authentication.

---

## 🧠 Recommended Models

| Category | Model Name |
|-----------|-------------|
| ✅ Recommended | `Gensyn/Qwen2.5-0.5B-Instruct` |
| ✅ Recommended | `Qwen/Qwen3-0.6B` |
| 🧪 Optional | `nvidia/AceInstruct-1.5B` |
| 🧪 Optional | `dnotitia/Smoothie-Qwen3-1.7B` |
| 🧪 Optional | `Gensyn/Qwen2.5-1.5B-Instruct` |

---

## 🧾 Notes
- This setup guide is for **private use and internal testing only**.  
- Credit to the original authors of RL Swarm and the GenRL framework.  
- Base installation references: **arcxteam** & **gasoline**.

---

**© 2025 CHATGPT — Private Node Documentation**
