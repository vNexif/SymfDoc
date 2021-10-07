![](https://github.com/vNexif/SymfDoc/actions/workflows/docker-comp.yml/badge.svg)
#Sample Symfony project based on docker

### 1.Setup Docker and Docker-Compose:
[Docker Install](https://docs.docker.com/compose/install/) <- Instalation Guide @ [Docker Docs](https://docs.docker.com)
```shell
    sudo apt-get update
    sudo apt-get install \
        apt-transport-https \
        ca-certificates \
        curl \
        gnupg \
        lsb-release
    
    curl -fsSL https://download.docker.com/linux/debian/gpg | \
     sudo gpg --dearmor \
        -o /usr/share/keyrings/docker-archive-keyring.gpg


    echo \
        "deb [arch=$(dpkg --print-architecture) signed-by=/usr/share/keyrings/docker-archive-keyring.gpg] https://download.docker.com/linux/debian \
        $(lsb_release -cs) stable" | sudo tee /etc/apt/sources.list.d/docker.list > /dev/null

    sudo apt-get update
    sudo apt-get install docker-ce docker-ce-cli contrainerd.io


    sudo curl -L "https://github.com/docker/compose/releases/download/1.29.2/docker-compose-$(uname -s)-$(uname -m)" -o /usr/local/bin/docker-compose

    sudo chmod +x /usr/local/bin/docker-compose
```
### 2.Run Docker Containers:
```shell
    git clone https://github.com/vNexif/SymfDoc.git
    cd ./SymfDoc
    docker-compose up -d --build
```

### Optional:
Edit [Enviroment Variables](./.env) to change Nginx and PHP Versions.