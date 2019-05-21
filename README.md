# cheat-sheets

git diff
git show -f
pip freeze > requirements.txt
pip install -r requirements.txt

git config --global core.editor "code --wait"

git config user.name
cat ~/.gitconfig
git config --list
git config --global [--unset] [credential.helper]
git config --get-all credential.helper
git push -u origin master
git remote set-url origin https://github.com/opensourceaccount/angular-youtube-app.git

git config --add credential.helper ""
git config --replace-all credential.helper
git config --get-all credential.helper
git config --unset-all credential.helper

# SUBMODULES

### Starting with Submodules
    git submodule add <repo_url> [<path_to_submodule>]

    # git config submodule.<?? DbConnector ??>.url PRIVATE_URL

    git commit -am 'added <DbConnector> module'
    git push origin master

### Cloning a Project with Submodules
    git clone --recurse-submodules https://github.com/chaconinc/MainProject
OR
    git clone https://github.com/chaconinc/MainProject
    git submodule update [--init] [--remote] [--merge] [--recursive]     

### Pulling in Upstream Changes
```
    git submodule update [--init] [--remote] [--merge] [--recursive] 
```

### Aliases
    git config alias.sdiff '!'"git diff && git submodule foreach 'git diff'"
    git config alias.spush 'push --recurse-submodules=on-demand'
    git config alias.supdate 'submodule update --remote --merge'

    git config --global alias.update '!git pull && git submodule update --init --recursive'

### Submodule Tips
    git submodule foreach 'git checkout -b featureA'