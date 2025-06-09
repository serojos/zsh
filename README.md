# zsh
Содержит **oh-my-zsh**, плагин **zsh-syntax-highlighting** и сконфигурированную тему **powerlevel10k**


## Источник (оригинал): 
https://github.com/ohmyzsh/ohmyzsh.git  
https://github.com/zsh-users/zsh-syntax-highlighting.git  
https://github.com/romkatv/powerlevel10k.git


## Установка
clone git@github.com:serojos2/zsh.git /usr/bin/.oh-my-zsh  
cp /usr/bin/.oh-my-zsh/.zshrc ~/.zshrc  
nano ~/.rc  
exec zsh  


## Initial Setup
cd /usr/bin  
git clone https://github.com/ohmyzsh/ohmyzsh.git /usr/bin/.oh-my-zsh  
rm -rf /usr/bin/.oh-my-zsh/.git  
git clone --depth=1 https://github.com/romkatv/powerlevel10k.git /usr/bin/.oh-my-zsh/themes/powerlevel10k  
rm -rf /usr/bin/.oh-my-zsh/themes/powerlevel10k/.git  
git clone https://github.com/zsh-users/zsh-syntax-highlighting.git /usr/bin/.oh-my-zsh/plugins/zsh-syntax-highlighting  
rm -rf /usr/bin/.oh-my-zsh/plugins/zsh-syntax-highlighting/.git  

**Выбери настройки, а на вопрос сохранить ли конфигу в .zshrc ответь No**  
exec zsh  

nano ~/.zshrc  
cp ~/.zshrc $ZSH/.zshrc  
cat ~/.p10k.zsh >$ZSH/themes/powerlevel10k/zshrc-p10k.zsh  

git init  
git remote add origin git@github.com:serojos2/zsh.git  
git add .  
git commit -m "Init Commit"  
git push origin HEAD  
