# Terminal

## Graphics Drivers

First of all, let's install the graphics drivers:
- Follow the commands and instructions according to your graphics provider: https://github.com/ValveSoftware/Proton/wiki/Requirements. 

    In my case, my computer has an **AMD Radeon** graphics hardware:
    ```
    sudo add-apt-repository ppa:kisak/kisak-mesa
    sudo apt dist-upgrade
    sudo apt install mesa-vulkan-drivers mesa-vulkan-drivers:i386
    ```
    

## Git and Curl

Let's install git first because it will be used to install other features and programs:
```
sudo apt install git
```

Let's also install curl for the same reason above:
```
sudo apt install curl
``` 


## Terminal Zsh and Oh My Zsh franework

Let's improve the terminal by installing and changing the main shell to ZSH, adding the Oh My Zsh framework and then add some themes like Spaceship:
- Official site: https://github.com/ohmyzsh/ohmyzsh/wiki/Installing-ZSH


### Zsh

First, let's check if the Zsh is installed:
```
zsh --version
``` 
> *Expected result: `zsh 5.4.2` or more recent.*

If zsh is not found, let's install by typing the following command:
```
sudo apt install zsh
```

Make it your default shell by running the command below:
```
chsh -s $(which zsh)
```

Restart your computer and check your terminal to see if it works. You can double-check by typing `echo $SHELL`. The value returned must be `/bin/zsh`.


### Oh My Zsh
Oh-my-zsh provides an installer script for installing the framework, and we need to install some other required packages, including wget for downloading the installer script and Git for downloading oh-my-zsh shell from GitHub.

```
sudo apt install wget git
```

Now download the installer script and execute it.
```
wget https://github.com/robbyrussell/oh-my-zsh/raw/master/tools/install.sh -O - | zsh
```

Next, we need to create a new configuration for zsh. As with the Bash shell, which has a configuration named '.bashrc', for zsh, we need a '.zshrc' configuration file. It's available in the oh-my-zsh templates directory.

Copy the template .zshrc.zsh-template configuration file to the home directory .zshrc and apply the configuration by running the source command, as shown below.

```
cp ~/.oh-my-zsh/templates/zshrc.zsh-template ~/.zshrc
source ~/.zshrc
```

### Spaceship Theme for Oh-My-Zsh

First let's clone Spaceship repository to the ZSH themes folder:
```
git clone https://github.com/denysdovhan/spaceship-prompt.git "$ZSH_CUSTOM/themes/spaceship-prompt"
```

Then, let's create a symblink to the Zsh theme for the Oh My Zsh themes folder:
```
ln -s "$ZSH_CUSTOM/themes/spaceship-prompt/spaceship.zsh-theme" "$ZSH_CUSTOM/themes/spaceship.zsh-theme"
```

Now, let's change ZSH Theme by changing the `~/.zshrc` file. You can use any editor of your choice. In my case I am using Visual Studio Code:
```
code ~/.zshrc
``` 
Change the value of variable `ZSH_THEME` to `"spaceship"`:
```
ZSH_THEME="spaceship"
``` 
#### Additional configurations

Let's use the power of spaceship theme by adding some additional configuraitons: 

At the end of the file `~/.zshrc`, add the following lines:
```
SPACESHIP_PROMPT_ORDER=(
  user          # Username section
  dir           # Current directory section
  host          # Hostname section
  git           # Git section (git_branch + git_status)
  hg            # Mercurial section (hg_branch  + hg_status)
  exec_time     # Execution time
  line_sep      # Line break
  vi_mode       # Vi-mode indicator
  jobs          # Background jobs indicator
  exit_code     # Exit code section
  char          # Prompt character
)
SPACESHIP_USER_SHOW=always
SPACESHIP_PROMPT_ADD_NEWLINE=false
SPACESHIP_CHAR_SYMBOL="❯"
SPACESHIP_CHAR_SUFFIX=" "
```

### Puglins for ZSH

You can add very useful plugins to your zsh to improve your speed while using terminal.
Let's add some very cool plugins to auto-complete, syntax highlighting, auto-suggestions:

First, we need to install Zinit:
```
sh -c "$(curl -fsSL https://git.io/zinit-install)"
```

Then, let's open our `~/.zshrc` file again and add the following lines at the end:
```
zinit light zdharma-continuum/fast-syntax-highlighting
zinit light zsh-users/zsh-autosuggestions
zinit light zsh-users/zsh-completions
```

## Dracula Theme

Open the website: https://draculatheme.com/gnome-terminal to check the documentation.

This theme can be installed on Gnome 3 terminal and any other Gnome based terminal program like the Unity terminal bundled with Ubuntu.

You'll need the dconf command (if you run a recent Gnome version). In Ubuntu,this can be installed by running:
```
sudo apt-get install dconf-cli
```
In other distros you'll need to dig around to find it, search your repositories for dconf related packages.

After installing dconf, you can clone this repository to your machine.
```
git clone https://github.com/dracula/gnome-terminal
cd gnome-terminal
```

Then you can run the installation script:
```
./install.sh
```

