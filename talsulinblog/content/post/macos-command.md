---
title: "terminal command"
date: 2023-03-16T13:00:00-06:00
tags: [learning, tutorial]
show_summary: false 
---

## WSL&Clash
### create `~/.proxy` file
```shell
touch ~/.proxy
```

### adding codes in `~/.proxy` file
```shell
#!/bin/bash
hostip=$(cat /etc/resolv.conf |grep -oP '(?<=nameserver\ ).*')
export https_proxy="http://${hostip}:7890"
export http_proxy="http://${hostip}:7890"
export all_proxy="socks5://${hostip}:7890"
```
### edit `.zshrc` or `.bashrc` file
```shell
source ~/.proxy
```

### conda & cudatoolkit & cudnn & pytorch
```shell
#conda
curl -L -O "https://github.com/conda-forge/miniforge/releases/latest/download/Mambaforge-$(uname)-$(uname -m).sh"
bash Mambaforge-$(uname)-$(uname -m).sh
#cudatoolkit
wget https://developer.download.nvidia.com/compute/cuda/repos/wsl-ubuntu/x86_64/cuda-keyring_1.0-1_all.deb
sudo dpkg -i cuda-keyring_1.0-1_all.deb
sudo apt-get update
sudo apt-get -y install cuda
#cudnn
sudo apt install nvidia-cudnn  
#pytorch
conda install pytorch torchvision torchaudio pytorch-cuda=11.7 -c pytorch -c nvidia  
```



## Building terminal

### install oh-my-zsh
```shell
sh -c "$(curl -fsSL https://raw.githubusercontent.com/ohmyzsh/ohmyzsh/master/tools/install.sh)"
```
### install powerlevel10k
```shell
git clone --depth=1 https://github.com/romkatv/powerlevel10k.git ${ZSH_CUSTOM:-$HOME/.oh-my-zsh/custom}/themes/powerlevel10k
```
Set `ZSH_THEME="powerlevel10k/powerlevel10k"` in `~/.zshrc`.

### install powerlevel10k plugins
#### install zsh-autosuggestions
```shell
git clone https://github.com/zsh-users/zsh-autosuggestions ${ZSH_CUSTOM:-~/.oh-my-zsh/custom}/plugins/zsh-autosuggestions
```
#### install zsh-syntax-highlighting
```shell
git clone https://github.com/zsh-users/zsh-syntax-highlighting.git ${ZSH_CUSTOM:-~/.oh-my-zsh/custom}/plugins/zsh-syntax-highlighting
```
#### install zsh-z
```shell
git clone https://github.com/agkozak/zsh-z ${ZSH_CUSTOM:-~/.oh-my-zsh/custom}/plugins/zsh-z
```
#### adding plugins array in `.zshrc`
```shell
plugins=(
  git
  zsh-autosuggestions
  zsh-syntax-highlighting
  zsh-z
)
```

## Silicon
### show COM devices
```shell
ls /dev/tty.*
#also ls /dev/cu.*
```

### run exe file
```shell
/Users/sulin/Desktop/ula1x4rtb -u /dev/cu.usbmodem0004401671811 | tee ~/Desktop/out.txt
#file_path COM_port | output_file
```
