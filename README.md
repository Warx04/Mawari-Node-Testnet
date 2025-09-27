# Mawari-Node-Testnet

![GYfDNY-WcAAzeuB](https://github.com/user-attachments/assets/e592cc0e-f2a7-41be-bf8a-32416b4189c7)

---

## How to Run Guardian Node Testnet

*(Just follow the steps 1–4 below)*

1. [Mint NFT Guardian Node](#1-mint-nft-guardian-node)
2. [Run Guardian Node](#2-run-guardian-node)
3. [Delegate Guardian Node](#3-delegate-guardian-node)
4. [Submit Guardian Node Form](#4-submit-guardian-node-form)

---

## 1. Mint NFT Guardian Node

### A. Go to [https://testnet.mawari.net/mint](https://testnet.mawari.net/mint) and connect your wallet

![Mawari Guide 1](https://github.com/user-attachments/assets/2b6b7ad1-e607-4106-ba07-616ba53d86ce)
![Mawari Guide 2](https://github.com/user-attachments/assets/a314abe0-38fb-4764-8840-409bc99d0827)
![Mawari Guide 3](https://github.com/user-attachments/assets/1c47705b-d449-48f8-b9e9-eb445df04e9b)

### B. Claim Faucet Mawari

![Mawari Guide 4](https://github.com/user-attachments/assets/dd74364f-5842-45e8-bfe6-2b108b1bcabd)
![Mawari Guide 7](https://github.com/user-attachments/assets/95bb4bb0-6557-4bb5-87ff-6e01adc25de0)
![Mawari Guide 8](https://github.com/user-attachments/assets/952d4eb9-9f58-49fd-b8f7-99d04b362c80)

### C. Mint Guardian Node NFT

* **Set to max claim: 3**

![Mawari Guide 5](https://github.com/user-attachments/assets/376c4d83-73e8-47a1-8498-6a0048d4fd3c)
![Mawari Guide 6](https://github.com/user-attachments/assets/7d75c479-b4e8-4383-86c7-a5e82db92c8f)
![Mawari Guide 10](https://github.com/user-attachments/assets/e5eeac4a-e22a-491d-97e9-4f5937ddc256)

---

## 2. Run Guardian Node

### 🖥️ Minimum VPS Requirements

| Resource             | Requirement                         |
| -------------------- | ----------------------------------- |
| ⚡ CPU                | 2 vCPU                              |
| 💾 RAM               | 4 GB                                |
| 📦 Storage           | 75 GB                               |
| 🌐 Bandwidth         | 100 Mbps                            |
| 🖥️ Operating System | Ubuntu 22.04 / 24.04, Windows 10/11 |

> **Note:** Higher specs = better stability and potentially more rewards.

---

### Install Packages

```bash
sudo apt-get update && sudo apt-get upgrade -y
sudo apt install curl ufw iptables build-essential git wget lz4 jq make gcc nano automake autoconf tmux htop nvme-cli \
libgbm1 pkg-config libssl-dev libleveldb-dev tar clang bsdmainutils ncdu unzip -y
```

---

### Install Docker

```bash
sudo apt update -y && sudo apt upgrade -y
for pkg in docker.io docker-doc docker-compose podman-docker containerd runc; do sudo apt-get remove $pkg; done

sudo apt-get update
sudo apt-get install ca-certificates curl gnupg -y
sudo install -m 0755 -d /etc/apt/keyrings
curl -fsSL https://download.docker.com/linux/ubuntu/gpg | sudo gpg --dearmor -o /etc/apt/keyrings/docker.gpg
sudo chmod a+r /etc/apt/keyrings/docker.gpg

echo \
  "deb [arch=$(dpkg --print-architecture) signed-by=/etc/apt/keyrings/docker.gpg] \
  https://download.docker.com/linux/ubuntu $(. /etc/os-release && echo "$VERSION_CODENAME") stable" | \
  sudo tee /etc/apt/sources.list.d/docker.list > /dev/null

sudo apt update -y && sudo apt upgrade -y
sudo apt-get install docker-ce docker-ce-cli containerd.io docker-buildx-plugin docker-compose-plugin -y

# Test Docker
sudo docker run hello-world
```

---

### Install Guardian Node

```bash
mkdir mawari && cd mawari
nano docker-compose.yaml
```

Paste the following configuration:

```yaml
services:
  guardian-node:
    image: us-east4-docker.pkg.dev/mawarinetwork-dev/mwr-net-d-car-uses4-public-docker-registry-e62e/mawari-node:latest
    container_name: guardian-node
    restart: always
    environment:
      - OWNERS_ALLOWLIST=YOUR_EVM_ADDRESS_HERE # <-- change your EVM address here 
    volumes:
      - ./cache:/app/cache
```

Save the file: `CTRL + X`, then press `Y`, then `ENTER`.

---

### Start Your Node

```bash
docker compose up -d
```

---

### Check Logs

```bash
docker compose logs -f
```

> Do not exit the logs yet. You will need them to check the delegate process.

* After running the node, you will get a **Burner Address**. Copy and save it — you will need it for delegation.
* Send **1 Mawari Faucet** to your **Burner Address** from your **Owner Address**.

![Mawari Node 2](https://github.com/user-attachments/assets/a07a997a-fb17-40d3-9427-03d7b9d0a6bf)

<img width="1312" height="610" alt="image" src="https://github.com/user-attachments/assets/380112d3-00f1-4ab8-9b13-6ab92057f09c" />

---

## 3. Delegate Guardian Node

### A. Fund Burner Address

Before delegation, make sure your **Burner Address** has received **1 Mawari Faucet** from your **Owner Address**.

### B. Open Delegation Page

Go to [https://app.testnet.mawari.net/licenses](https://app.testnet.mawari.net/licenses) and connect your wallet.

<img width="1319" height="410" alt="image" src="https://github.com/user-attachments/assets/565719f9-fe96-40f2-954c-8be11c5a3559" />
<img width="400" height="559" alt="image" src="https://github.com/user-attachments/assets/e5ef791b-8402-401a-8994-e61ec52515c6" />
<img width="876" height="511" alt="image" src="https://github.com/user-attachments/assets/934e62e7-eee9-45db-9fb6-f4ebefa2efaa" />

### C. Delegate Node

* Checklist all License IDs and click **Delegate**.
* Paste your **Burner Address**.

<img width="1300" height="446" alt="image" src="https://github.com/user-attachments/assets/ac4c7096-6972-4aa5-89e1-f8f4fd299475" />
<img width="1304" height="442" alt="image" src="https://github.com/user-attachments/assets/5bae04fc-6d45-438e-a03e-b5710c223689" />
<img width="1335" height="472" alt="image" src="https://github.com/user-attachments/assets/0fef2637-4cb6-4dda-937d-027fa00a5eae" />

* Watch the logs until you see the **submit delegate** confirmation.

<img width="712" height="163" alt="image" src="https://github.com/user-attachments/assets/88bf1152-abcf-4b85-8214-a36d4995d151" />

* After that, wait until the status changes from **Nodelegate** → **Pending** → **Running**.

<img width="1304" height="448" alt="image" src="https://github.com/user-attachments/assets/a77fc35c-403b-4f5d-87d9-43d00945e4cd" />

✅ **Done! You have successfully run Mawari Node Testnet.**
⏳ Rewards (zMawari) will appear after ~24 hours. Higher specs = more potential earnings.

---

## 4. Submit Guardian Node Form

After successfully running the node, submit the confirmation form here:
👉 [https://docs.google.com/forms/d/e/1FAIpQLScn-qN1oNbd_At0UEIK5bJFPlEEouGh49f_MWHS7nhGeNDe8A/viewform](https://docs.google.com/forms/d/e/1FAIpQLScn-qN1oNbd_At0UEIK5bJFPlEEouGh49f_MWHS7nhGeNDe8A/viewform)

<img width="682" height="338" alt="image" src="https://github.com/user-attachments/assets/87af8bd6-1e0b-4e0c-9e20-7d94031284cb" />

---
