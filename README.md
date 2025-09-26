# Mawari-Node-Testnet
![GYfDNY-WcAAzeuB](https://github.com/user-attachments/assets/e592cc0e-f2a7-41be-bf8a-32416b4189c7)

---

## How To Running Guardian Node Testnet 

*( Just Follow The Step 1-4 Below )*

1. [Mint NFT Guardian Node](#1-mint-nft-guardian-node)
2. [Run Guardian Node](#2-run-guardian-node)
3. [Delegate Guardian Node](3-delegate-guardian-node)
4. [Submit Form Guardian Node](4-submit-form-guardian-node)

## 1. Mint NFT Guardian Node

### A. Go to https://testnet.mawari.net/mint Connect Your Wallet
![Mawari Guide 1](https://github.com/user-attachments/assets/2b6b7ad1-e607-4106-ba07-616ba53d86ce)
![Mawari Guide 2](https://github.com/user-attachments/assets/a314abe0-38fb-4764-8840-409bc99d0827)
![Mawari Guide 3](https://github.com/user-attachments/assets/1c47705b-d449-48f8-b9e9-eb445df04e9b)

### B. Claim Your Faucet Mawari

![Mawari Guide 4](https://github.com/user-attachments/assets/dd74364f-5842-45e8-bfe6-2b108b1bcabd)
![Mawari Guide 7](https://github.com/user-attachments/assets/95bb4bb0-6557-4bb5-87ff-6e01adc25de0)
![Mawari Guide 8](https://github.com/user-attachments/assets/952d4eb9-9f58-49fd-b8f7-99d04b362c80)

### C. Mint Guardian Node NFT

- *Set To max claim **3**
  
  ![Mawari Guide 5](https://github.com/user-attachments/assets/376c4d83-73e8-47a1-8498-6a0048d4fd3c)
  ![Mawari Guide 6](https://github.com/user-attachments/assets/7d75c479-b4e8-4383-86c7-a5e82db92c8f)
  ![Mawari Guide 10](https://github.com/user-attachments/assets/e5eeac4a-e22a-491d-97e9-4f5937ddc256)

---

## 2. Run Guardian Node

### 🖥️ Minimum Requirement  

| Resource         | Requirement         |
|------------------|---------------------|
| ⚡ CPU           | 2 vCPU              |
| 💾 RAM           | 4 GB                |
| 📦 Storage       | 75 GB               |
| 🌐 Bandwidth     | 100 Mbps            |
| 🖥️ Operating System | Ubuntu 22.04 / 24.04, Windows 10/11 |

---

### Install Package 

```bash
sudo apt-get update && sudo apt-get upgrade -y
```
```bash
sudo apt install curl ufw iptables build-essential git wget lz4 jq make gcc nano automake autoconf tmux htop nvme-cli libgbm1 pkg-config libssl-dev libleveldb-dev tar clang bsdmainutils ncdu unzip libleveldb-dev  -y
```

---

### Install Docker

```bash
sudo apt update -y && sudo apt upgrade -y
for pkg in docker.io docker-doc docker-compose podman-docker containerd runc; do sudo apt-get remove $pkg; done

sudo apt-get update
sudo apt-get install ca-certificates curl gnupg
sudo install -m 0755 -d /etc/apt/keyrings
curl -fsSL https://download.docker.com/linux/ubuntu/gpg | sudo gpg --dearmor -o /etc/apt/keyrings/docker.gpg
sudo chmod a+r /etc/apt/keyrings/docker.gpg

echo \
  "deb [arch="$(dpkg --print-architecture)" signed-by=/etc/apt/keyrings/docker.gpg] https://download.docker.com/linux/ubuntu \
  "$(. /etc/os-release && echo "$VERSION_CODENAME")" stable" | \
  sudo tee /etc/apt/sources.list.d/docker.list > /dev/null

sudo apt update -y && sudo apt upgrade -y

sudo apt-get install docker-ce docker-ce-cli containerd.io docker-buildx-plugin docker-compose-plugin

# Test Docker
sudo docker run hello-world
```

---


### Install Guardian Node 

```bash
mkdir mawari
```
```bash
cd mawari
```
```bash
nano docker-compose.yaml
```

---

### Paste all this docker setting 

```yaml
services:
  guardian-node:
    image: us-east4-docker.pkg.dev/mawarinetwork-dev/mwr-net-d-car-uses4-public-docker-registry-e62e/mawari-node:latest
    container_name: guardian-node
    restart: always
    environment:
      - OWNERS_ALLOWLIST=YOUREVMADDRESSHERE # <-- change your evm address here 
    volumes:
      - ./cache:/app/cache
```
Save file: `CTRL + X`, then press `Y`, then `ENTER`.

---

### Start Your Node 

```bash
docker compose up -d
```
`You should fast open the logs`

---

### Check Logs

```bash
docker compose logs -f
```
`After you running the node, you got BURNER ADDRESS, Please Copy And Save The Burner address to delegate your node`

![Mawari Node 2](https://github.com/user-attachments/assets/a07a997a-fb17-40d3-9427-03d7b9d0a6bf)







