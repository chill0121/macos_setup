# macOS Setup

This repository is for setting up a new MacBook with various settings and applications I've grown to like.

## Table of Contents

- [List of Applications](#list-of-applications)
- [Initial Setup](#initial-setup)
- [Installations](#installations)
  - [Google Chrome](#google-chrome)
  - [Nerd Fonts](#nerd-fonts)
  - [Hyper](#hyper)
  - [Warp](#warp)
  - [fish](#fish)
  - [Oh My Posh](#oh-my-posh)
  - [GitHub Desktop](#github-desktop)
  - [GitHub CLI](#github-cli)
  - [Amazon Workspaces](#amazon-workspaces)
  - [VS Code](#vs-code)
  - [Magnet](#magnet)
  - [Maccy](#maccy)
  - [AWS CLI](#aws-cli)
  - [pyenv and Python](#pyenv-and-python)
  - [pipenv](#pipenv)
  - [PySpark](#pyspark)
  - [glances](#glances)
  - [Discord](#discord)
  - [Obsidian](#obsidian)
  - [Docker](#docker)

# List of Applications

## Package Manager
- Homebrew

## Web Browser
- Google Chrome

## Terminal & Shell
- Hyper
- Warp
- fish
- Oh My Posh
- Nerd Fonts

## Development Tools
- GitHub Desktop
- GitHub CLI
- VS Code
- AWS CLI
- Docker

## Python Development
- pyenv
- Python
- pipenv
- PySpark

## Productivity & Utilities
- Magnet (window management)
- Maccy (clipboard manager)
- glances (system monitoring)
- Obsidian (note-taking)

## Communication & Work
- Amazon Workspaces
- Discord

# Initial Setup

The installation of applications utilizes Homebrew as the package manager for macOS. It is best practice to use a package manager for easier installation and keeping your applications up to date.

## 1. Install Homebrew

```bash
/bin/bash -c "$(curl -fsSL https://raw.githubusercontent.com/Homebrew/install/HEAD/install.sh)"
```

## 2. Configure Automatic Updates for Homebrew

```bash
brew autoupdate start --upgrade --cleanup --enable-notification
```

# Installations

## Google Chrome

1. Install Google Chrome

```bash
brew install --cask google-chrome
```

2. Login to Google Chrome

## Nerd Fonts

https://www.nerdfonts.com/font-downloads

```bash
brew tap homebrew/cask-fonts
brew install --cask font-hack-nerd-font
```

## Hyper

1. Install Hyper

```bash
brew install --cask hyper
hyper install hyper-material-theme
```

## Warp

https://www.warp.dev/

1. Install Warp

```bash
brew install --cask warp
mkdir -p ~/.warp/themes
cd ~/.warp/themes
curl -O "https://raw.githubusercontent.com/chill0121/warp_theme_hyper_material/main/hyper_material.yaml"
cd ~
```

2. After installing, open Warp and go to Settings > Themes > Import Theme and select the hyper_material.yaml file.

## fish

https://fishshell.com/

1. Install fish and set it as the default shell

```bash
brew install fish
sudo bash -c 'echo /opt/homebrew/bin/fish >> /etc/shells'
chsh -s /opt/homebrew/bin/fish
```

2. Set up fish to have brew in the path and update completions

```bash
fish_add_path /opt/homebrew/bin
fish_update_completions
```

3. Set up fish to run oh-my-posh and have all functions

```bash
touch ~/.config/fish/config.fish
cp -R ~/code/macos_setup/.config/fish/* ~/.config/fish/
```

## Oh My Posh

1. Install Oh My Posh

```bash
brew tap jandedobbeleer/oh-my-posh
brew install oh-my-posh
mkdir ~/.poshthemes
cd ~/.poshthemes
curl -O "https://raw.githubusercontent.com/chill0121/macos_setup/main/.poshthemes/octo-theme.omp.json"
oh-my-posh init fish --config ~/.poshthemes/octo-theme.omp.json | source
cd ~
```

2. Reload your terminal
3. Verify that the theme is working by running `oh-my-posh --version`

## GitHub Desktop

1. Install GitHub Desktop

```bash
brew install --cask github
```

2. Run GitHub Desktop
3. Login to GitHub

## GitHub CLI

```bash
brew install gh
```

## Amazon Workspaces

```bash
brew install --cask amazon-workspaces
```

## VS Code

1. Install VS Code

```bash
brew install --cask visual-studio-code
```

2. Login to GitHub in VS Code to synchronize settings and extensions

## Magnet

1. Install Magnet from the Mac App Store: https://apps.apple.com/us/app/magnet/id441258766?mt=12
2. Open Magnet
3. Follow the setup instructions to enable Magnet to control your windows

## Maccy

```bash
brew install --cask maccy
```

## AWS CLI

```bash
brew install awscli
```

## pyenv and Python

Reference: https://hackernoon.com/reaching-python-development-nirvana-bb5692adf30c

```bash
brew install pyenv
pyenv install {python_version}    # Install specific Python version
pyenv global {python_version}     # Set global Python version
pyenv local {python_version}      # Set local Python version for current directory
```

**Note:** Replace `{python_version}` with the desired Python version. Check available versions with `pyenv install --list`.

## pipenv

Reference: https://hackernoon.com/reaching-python-development-nirvana-bb5692adf30c

```bash
brew install pipenv
```

To create a new project and install packages:

```bash
cd your-project-directory
pipenv install                    # Create virtual environment
pipenv install requests pandas   # Install specific packages
pipenv shell                     # Activate virtual environment
```

## PySpark

PySpark requires Java to be installed. This setup installs Java and configures PySpark for big data processing.

### 1. Install Java (OpenJDK)

```bash
brew install openjdk@17
```

**Note:** Using OpenJDK 17 instead of 24 for better PySpark compatibility.

### 2. Create Java symlink

```bash
sudo ln -sfn /opt/homebrew/opt/openjdk@17/libexec/openjdk.jdk /Library/Java/JavaVirtualMachines/openjdk-17.jdk
```

### 3. Set JAVA_HOME environment variable

Edit `~/.config/fish/config.fish` and add this line:

```bash
set -gx JAVA_HOME /opt/homebrew/opt/openjdk@17/libexec/openjdk.jdk/Contents/Home
```

### 4. Install PySpark

If using pipenv:

```bash
pipenv install pyspark
```

### 5. Verify installation

```bash
python -c "import pyspark; print(pyspark.__version__)"
```

**Note:** Restart your terminal after setting JAVA_HOME to ensure the environment variable is loaded.

## glances

A cross-platform system monitoring tool.

```bash
brew install glances
```

Run glances to monitor your system:

```bash
glances
```

## Discord

```bash
brew install --cask discord
```

## Obsidian

```bash
brew install --cask obsidian
```

## Docker

Install Docker Desktop (GUI application):

```bash
brew install --cask docker-desktop
```

Install Docker CLI:

```bash
brew install docker
```