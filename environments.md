## Zsh
```
apt-get update
apt-get install zsh
sh -c "$(curl -fsSL https://raw.githubusercontent.com/robbyrussell/oh-my-zsh/master/tools/install.sh)"
git clone https://github.com/zsh-users/zsh-autosuggestions ${ZSH_CUSTOM:-~/.oh-my-zsh/custom}/plugins/zsh-autosuggestions
git clone https://github.com/zsh-users/zsh-syntax-highlighting.git ${ZSH_CUSTOM:-~/.oh-my-zsh/custom}/plugins/zsh-syntax-highlighting
vi ~/.zshrc
```

Edit to the following:
```
ZSH_THEME="ys"

plugins=(
  git
  zsh-autosuggestions
  zsh-syntax-highlighting
)
```
 
## Vim
```
mkdir -p ~/.vim/autoload ~/.vim/bundle && \
curl -LSso ~/.vim/autoload/pathogen.vim https://tpo.pe/pathogen.vim
git clone git://github.com/altercation/vim-colors-solarized.git ~/.vim/bundle/vim-colors-solarized
vi ~/.vimrc
```

Add the following:
```
execute pathogen#infect()
filetype plugin indent on
set nu
set ru
syntax on
set t_Co=256
set background=dark
colorscheme solarized
```

## Docker
```
apt-get install docker.io
apt-get install python-pip
pip install docker-compose
```
