## Prerequisite
- **Update packages**
    ```
    sudo apt update && sudo apt upgrade -y
    ```
- **Install dependencies**
     ```
     sudo apt install curl build-essential git wget jq make gcc tmux ca-certificates curl -y
     ```
- **Install docker**
    ```
    for pkg in docker.io docker-doc docker-compose docker-compose-v2 podman-docker containerd runc; do sudo apt-get remove -qy $pkg; done

    sudo install -m 0755 -d /etc/apt/keyrings
    sudo curl -fsSL https://download.docker.com/linux/ubuntu/gpg -o /etc/apt/keyrings/docker.asc
    sudo chmod a+r /etc/apt/keyrings/docker.asc

    echo \
      "deb [arch=$(dpkg --print-architecture) signed-by=/etc/apt/keyrings/docker.asc] https://download.docker.com/linux/ubuntu \
      $(. /etc/os-release && echo "$VERSION_CODENAME") stable" | \
      sudo tee /etc/apt/sources.list.d/docker.list > /dev/null
    sudo apt-get update
    sudo apt-get install -qy docker-ce docker-ce-cli containerd.io docker-buildx-plugin docker-compose-plugin
    sudo systemctl start docker
    ```

- **Run Docker as a non-root user**
    ```
    sudo chmod 666 /var/run/docker.sock
    sudo usermod -aG docker <your_user>
    ```

### Relogin to your server to take effect from usermod !!!

## Install and Run
- **Clone this repo to your server**
    ```
    git clone https://github.com/CryptoNodeID/sepolia-arb.git
    cd sepolia-arb
    ```
- **Create necessary folders**
    ```
    mkdir -p $home/sepolia-arb/arb-data
    ```
- **Start all docker containers**
    ```
    docker compose up -d
    ```
- **To check the logs**
    ```
    docker compose logs -f
    ```
