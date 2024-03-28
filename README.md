# zsh_setting

Due to work requirements, I need to install Zsh and Oh My Zsh in the WSL environment. This README records how to do it.

## Prerequisite

```bash
// update/upgrade
sudo apt-get update
sudo apt-get upgrade

// some of useful tool
sudo apt install vim curl git
```


## ZSH

```bash
// install zsh
sudo apt install zsh

// check if installed
cat /etc/shells

// setting zsh as the default shell
sudo chsh -s $(which zsh)

// checking if the shell is zsh
echo $0
```

## Oh my zsh
[Oh My Zsh](https://github.com/ohmyzsh/ohmyzsh) is a delightful, open source, community-driven framework for managing your Zsh configuration.

```bash
sh -c "$(curl -fsSL https://raw.githubusercontent.com/ohmyzsh/ohmyzsh/master/tools/install.sh)"
```

## powerlevel10k
[Powerlevel10k](https://github.com/romkatv/powerlevel10k) is a theme for Zsh.

```bash
// install through Oh My Zsh
git clone --depth=1 https://github.com/romkatv/powerlevel10k.git ${ZSH_CUSTOM:-$HOME/.oh-my-zsh/custom}/themes/powerlevel10k
```

After installed, modify the configure in `.zshrc`. It's usually at `~/.zshrc`
```bash
ZSH_THEME="powerlevel10k/powerlevel10k"
```

Then, either restart the terminal or do the command
```
source ~/.zshrc
```

Finally, using prompt to do the basic setting you like
```
p10k configure
```

## Font
This is optional, but recommended.

  * [MesloLGS NF Regular.ttf](https://github.com/romkatv/powerlevel10k-media/raw/master/MesloLGS%20NF%20Regular.ttf)
  * [MesloLGS NF Bold.ttf](https://github.com/romkatv/powerlevel10k-media/raw/master/MesloLGS%20NF%20Bold.ttf)
  * [MesloLGS NF Italic.ttf](https://github.com/romkatv/powerlevel10k-media/raw/master/MesloLGS%20NF%20Italic.ttf)
  * [MesloLGS NF Bold Italic.ttf](https://github.com/romkatv/powerlevel10k-media/raw/master/MesloLGS%20NF%20Bold%20Italic.ttf)

At windows terminal

  1. press `Settings`
  2. Select the profile `Ubuntu`(or other linux you used) at the left menu.
  3. Scroll down to the `Additional settings` and click `Appearance`
  4. Change the `Font face`

## Zsh Plugins

### zsh-completions
* Clone the repository inside your oh-my-zsh repo:
```bash
git clone https://github.com/zsh-users/zsh-completions ${ZSH_CUSTOM:-${ZSH:-~/.oh-my-zsh}/custom}/plugins/zsh-completions
```
* Add it to `FPATH` in your `.zshrc` by adding the following line before `source "$ZSH/oh-my-zsh.sh"`:
```bash
fpath+=${ZSH_CUSTOM:-${ZSH:-~/.oh-my-zsh}/custom}/plugins/zsh-completions/src
```

### zsh-autosuggestions
* Clone this repository into `$ZSH_CUSTOM/plugins` (by default `~/.oh-my-zsh/custom/plugins`)
```bash
git clone https://github.com/zsh-users/zsh-autosuggestions ${ZSH_CUSTOM:-~/.oh-my-zsh/custom}/plugins/zsh-autosuggestions
```

### zsh-syntax-highlighting
* Clone this repository in oh-my-zsh's plugins directory:
```bash
git clone https://github.com/zsh-users/zsh-syntax-highlighting.git ${ZSH_CUSTOM:-~/.oh-my-zsh/custom}/plugins/zsh-syntax-highlighting
```

After installed, modify `.zshrc` and put plugins into configure. Here is my plugins
```bash
plugins=(
git
zsh-completions
zsh-autosuggestions
zsh-syntax-highlighting
pyenv
perl
)
```
