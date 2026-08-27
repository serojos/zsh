# zsh
Содержит **oh-my-zsh**, плагин **zsh-syntax-highlighting** и сконфигурированную тему **powerlevel10k**


## Источник (оригинал): 
https://github.com/ohmyzsh/ohmyzsh.git  
https://github.com/zsh-users/zsh-syntax-highlighting.git  
https://github.com/romkatv/powerlevel10k.git

## Установка
```
apt install -y zsh  
sed '/^root:/s/[^:]*$/\/usr\/bin\/zsh/' -i /etc/passwd  
git clone git@github.com:serojos2/zsh.git /opt/oh-my-zsh  
cp /opt/oh-my-zsh/.zshrc ~/.zshrc  
nano ~/.rc  
exec zsh 
```

### Файл .rc
```
export PGHOME=/var/lib/postgresql
source /opt/venv/bin/activate

# https://unix.stackexchange.com/questions/153862/remove-all-files-directories-except-for-one-file
# Включает поддержку команды rm -- ^file.txt , что удаляет всё кроме указанного файла
setopt extendedglob

alias chpg='chown -R postgres:postgres'
alias clip='xclip -selection clipboard'
alias pull='git pull origin main'
alias push='git push origin HEAD'
alias exp='/mnt/c/Windows/explorer.exe .'
alias py='python3'
alias rmz='rm *Zone.Identifier'
alias vpn="source /opt/vpn"

export C='/mnt/c'
export PF='/mnt/c/Program Files'
export D='/mnt/d'
export F='/mnt/f'

if nc -z -w1 192.168.50.8 2080 >/dev/null 2>&1; then
  export http_proxy="http://192.168.50.8:2080"
  export https_proxy="http://192.168.50.8:2080"
fi
```


## Как это собрано
```
cd /usr/bin  
git clone https://github.com/ohmyzsh/ohmyzsh.git /usr/bin/.oh-my-zsh  
rm -rf /usr/bin/.oh-my-zsh/.git  
git clone --depth=1 https://github.com/romkatv/powerlevel10k.git /usr/bin/.oh-my-zsh/themes/powerlevel10k  
rm -rf /usr/bin/.oh-my-zsh/themes/powerlevel10k/.git  
git clone https://github.com/zsh-users/zsh-syntax-highlighting.git /usr/bin/.oh-my-zsh/plugins/zsh-syntax-highlighting  
rm -rf /usr/bin/.oh-my-zsh/plugins/zsh-syntax-highlighting/.git  
```

**Выбери настройки, а на вопрос сохранить ли конфигу в .zshrc ответь No**  
```
exec zsh  

nano ~/.zshrc  
cp ~/.zshrc $ZSH/.zshrc  
cat ~/.p10k.zsh >$ZSH/themes/powerlevel10k/zshrc-p10k.zsh  

git init  
git remote add origin git@github.com:serojos2/zsh.git  
git add .  
git commit -m "Init Commit"  
git push origin HEAD  
```
