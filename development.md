# Development Environment

Install most common compilers and development dependencies:
```
sudo apt install build-essential default-jdk libssl-dev exuberant-ctags ncurses-term ack-grep silversearcher-ag fontconfig imagemagick libmagickwand-dev software-properties-common git vim-gtk3 curl
```

## ASDF

A single Package Manager for most common programming languages.
- Documentation: https://github.com/asdf-vm/asdf
- Follow the instructions at: https://asdf-vm.com/#/core-manage-asdf-vm

Clone only the latest branch:
```
git clone https://github.com/asdf-vm/asdf.git ~/.asdf --branch v0.7.8
```

Add to your shell:
```
echo -e "\n. $HOME/.asdf/asdf.sh" >> ~/.zshrc
```

Append completions to `fpath`:
```
echo -e "\nfpath=(${ASDF_DIR}/completions $fpath)" >> ~/.zshrc
```

Initialise completions with ZSH's `compinit`:
```
echo -e "\nautoload -Uz compinit && compinit" >> ~/.zshrc
```


## Installing NodeJS using ASDF

First of all, let's add the Node Js Plugin:
```
asdf plugin-add nodejs https://github.com/asdf-vm/asdf-nodejs.git
```

Import the Node.js release team's OpenPGP keys to main keyring:
```
bash ~/.asdf/plugins/nodejs/bin/import-release-team-keyring
```

Then, let's check the versions available:
```
asdf list-all nodejs
```

After that, install the nodejs specifying the version:
```
asdf install nodejs 13.12.0
```

Set your Global version of NodeJs:
```
asdf global nodejs 13.12.0
```

Don't forget to install NPM:
```
npm i npm
```

If you need to use another version of NodeJs in a project, you must install the required version and then in the project folder, you can run the following command:
```
asdf local nodejs 12.16.2
```


## Visual Studio Code
Development IDE: 
```
sudo snap install code --classic
```

## Git Kraken (optional)
I use GitKraken as a git IDE. It makes it easier to solve conflicts and merging for pull requests.

```
sudo snap install gitkraken
```

## Docker
Open the website: https://docs.docker.com/install and follow the steps according to your OS version.
- UBUNTU - Install Docker Engine - Community: 
  1. https://docs.docker.com/install/linux/docker-ce/ubuntu/
  2. https://docs.docker.com/install/linux/linux-postinstall/
  
  ### Ubuntu 19.10:

  - Docker CE is not available for **Ubuntu 19.10**. But you can install an older version: 
    
    - Adding dependencies first:
        ```
        sudo apt install apt-transport-https ca-certificates curl software-properties-common
        curl -fsSL https://download.docker.com/linux/ubuntu/gpg | sudo apt-key add -
        sudo add-apt-repository "deb [arch=amd64] https://download.docker.com/linux/ubuntu disco stable"
        ```
        - Now, check if Docker CE is available for your OS: 
        ```
        apt-cache search docker-ce
        ```
        - Install `Docker CE`:
        ```
        sudo apt install docker-ce
        ```

       - Creating grants to your user for using `docker`commnad without having to add `sudo`:
            ```
            sudo usermod -aG docker $USER && sudo systemctl enable docker
            ```
            > Restart your computer after executing this command.

    **Other OS versions:**
    - Run the following command:
        ```
        sudo apt update && sudo apt install apt-transport-https ca-certificates curl software-properties-common -y && curl -fsSL https://download.docker.com/linux/ubuntu/gpg | sudo apt-key add - && sudo apt-key fingerprint 0EBFCD88 && sudo add-apt-repository "deb [arch=amd64] https://download.docker.com/linux/ubuntu $(lsb_release -cs) stable" -y && sudo apt update && sudo apt install docker-ce -y
        ```

        - Creating grants to your user for using `docker`commnad without having to add `sudo`:
            ```
            sudo usermod -aG docker $USER && sudo systemctl enable docker
            ```
            > Restart your computer after executing this command.

    ### Docker Compose (optional)
    - Docs: https://docs.docker.com/compose/install/#install-compose
    
    If you'd like to install Docker Compose, follow the instructions below:
    ```
    sudo curl -L https://github.com/docker/compose/releases/download/1.21.2/docker-compose-`uname -s-uname -m` -o /usr/local/bin/docker-compose && sudo chmod +x /usr/local/bin/docker-compose && docker-compose --version
    ```
    
  
    ### Docker Portainer (optional): 
     - Docs: https://portainer.readthedocs.io/en/stable/
    
    If you would like to manage you containers in a visual way, you can install Docker Portainer:
    ```shell
    docker run --name portainer -d -p 9000:9000 -v /var/run/docker.sock:/var/run/docker.sock -v /opt/portainer:/data portainer/portainer
    ```
    
    