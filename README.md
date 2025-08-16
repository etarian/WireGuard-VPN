# WireGuard-VPN
This repository documents a step-by-step setup of a WireGuard VPN server on a DigitalOcean droplet and a Windows client.
1# Server Setup
<img width="2005" height="1160" alt="Screenshot 2025-08-16 123018" src="https://github.com/user-attachments/assets/f2c5ded2-2de8-499d-9a13-f0e95fdbc7be" />

1. SSH into DigitalOcean Droplet:
   ```bash
   ssh root@<YOUR_SERVER_IP>
sudo apt update
sudo apt install wireguard -y
<img width="702" height="618" alt="Screenshot 2025-08-16 112824" src="https://github.com/user-attachments/assets/b077ec0e-aa09-4c6e-aba2-4a3d240b8947" />
<img width="1209" height="1361" alt="Screenshot 2025-08-16 113031" src="https://github.com/user-attachments/assets/7e23c895-d36c-4805-a4ac-a2faea75e8cc" />
<img width="1082" height="977" alt="Screenshot 2025-08-16 113113" src="https://github.com/user-attachments/assets/57e248e0-9143-4671-9d63-c3cf665dd754" />

2# Client Setup (Windows)

1. Install WireGuard from [https://www.wireguard.com/install/](https://www.wireguard.com/install/)

2. Generate client keys (on server or client):
   ```bash
   wg genkey | tee client_private.key | wg pubkey > client_public.key
[Interface]
PrivateKey = <CLIENT_PRIVATE_KEY>
Address = 10.0.0.2/24
DNS = 1.1.1.1

[Peer]
PublicKey = <SERVER_PUBLIC_KEY>
Endpoint = <YOUR_SERVER_IP>:51820
AllowedIPs = 0.0.0.0/0
PersistentKeepalive = 25
ping 10.0.0.2
curl ifconfig.me
<img width="704" height="232" alt="Screenshot 2025-08-16 122917" src="https://github.com/user-attachments/assets/f10bebab-2a46-4471-ba0c-54da9a4222d8" />

