
# 💻 Setup Completo para Arch Linux (Python, Pyenv, ZSH, VS Code e mais)

Este guia traz um passo a passo para configurar um ambiente de desenvolvimento completo no **Arch Linux**, inspirado no script original para Ubuntu.

---

## 1️⃣ Atualizar Pacotes
```bash
sudo pacman -Syu --noconfirm
```

---

## 2️⃣ Instalar Python
> O Arch já traz o Python mais recente. Para múltiplas versões, utilize **Pyenv** (ver seção 4).
```bash
sudo pacman -S --noconfirm python python-pip python-pipx python-virtualenv
```

---

## 3️⃣ Pacotes Essenciais
```bash
sudo pacman -S --noconfirm git curl base-devel dkms perl wget \
gcc make mariadb-libs openssl zlib bzip2 readline sqlite llvm \
ncurses xz tk libffi lzma python-pyopenssl
```

---

## 4️⃣ Instalar Pyenv
```bash
curl -L https://github.com/pyenv/pyenv-installer/raw/master/bin/pyenv-installer | bash
```

Adicionar no **~/.zshrc** ou **~/.bashrc**:
```bash
export PATH="$HOME/.pyenv/bin:$PATH"
eval "$(pyenv init --path)"
eval "$(pyenv virtualenv-init -)"
```

Atualizar o shell:
```bash
source ~/.zshrc
```

---

## 5️⃣ Instalar VS Code
> Duas opções: versão open-source (`code`) ou a versão oficial da Microsoft (`visual-studio-code-bin`) via `yay`.

**Open-source:**
```bash
sudo pacman -S --noconfirm code
```

**Versão oficial (recomendada):**
```bash
yay -S --noconfirm visual-studio-code-bin
```

---

## 6️⃣ Instalar e Configurar ZSH
```bash
sudo pacman -S --noconfirm zsh
chsh -s /bin/zsh
zsh
```

**Oh-My-Zsh**
```bash
sh -c "$(curl -fsSL https://raw.github.com/ohmyzsh/ohmyzsh/master/tools/install.sh)"
```

---

## 7️⃣ Spaceship Prompt
```bash
git clone https://github.com/spaceship-prompt/spaceship-prompt.git "$ZSH_CUSTOM/themes/spaceship-prompt" --depth=1
ln -s "$ZSH_CUSTOM/themes/spaceship-prompt/spaceship.zsh-theme" "$ZSH_CUSTOM/themes/spaceship.zsh-theme"
```

Editar **~/.zshrc** e alterar:
```bash
ZSH_THEME="spaceship"
```

---

## 8️⃣ Plugins do ZSH

### Autosuggestions
```bash
git clone https://github.com/zsh-users/zsh-autosuggestions ${ZSH_CUSTOM:-~/.oh-my-zsh/custom}/plugins/zsh-autosuggestions
```

### Syntax Highlighting
```bash
git clone https://github.com/zsh-users/zsh-syntax-highlighting.git ${ZSH_CUSTOM:-~/.oh-my-zsh/custom}/plugins/zsh-syntax-highlighting
```

### Ativar Plugins
No **~/.zshrc**:
```bash
plugins=(git zsh-autosuggestions zsh-syntax-highlighting)
```

---

## 9️⃣ Fonte Powerline (Opcional)
```bash
mkdir -p ~/.fonts
git clone https://github.com/pdf/ubuntu-mono-powerline-ttf.git ~/.fonts/ubuntu-mono-powerline-ttf
fc-cache -vf
```

---

## 🔟 Finalizar
```bash
sudo reboot
```
