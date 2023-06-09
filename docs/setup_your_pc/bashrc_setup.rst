===============================================
Useful bashrc setup
===============================================

We advice that you add this elements to your bashrc to facilitate you your everyday life

Alias
===============================================

.. code::
    
    # some more ls aliases
    alias ll='ls -alF'
    alias la='ls -A'
    alias l='ls -CF'
    alias doc='cd ~/proj/knowledge_data_advisory'
    alias doccao='cd ~/perso/knowledge'
    alias phd='cd ~/perso/these-cao-tri-do/'
    alias proj='cd ~/proj'
    alias perso='cd ~/perso'
    alias g='gitui'
    alias gd='git diff'
    alias gs='git status'
    alias ga='git add .'
    alias gc='git commit -m'
    alias gp='git push'
    alias gf='git fetch'
    alias gr='git rebase'
    alias tig='tig --all'
    alias e="explorer.exe ."
    alias home='explorer.exe `wslpath -w ~/`'
    alias bashrc='code ~/.bashrc'
    alias pbi='cd ~/proj/knowledge_data_advisory/src/technology_inteligence'
    alias build_doc='sphinx-autobuild ~/proj/knowledge_data_advisory/ ~/proj/docs/_build/html'
    alias build_doccao='sphinx-autobuild ~/perso/knowledge/docs/source/ ~/perso/docs/_build/html'
    alias delete_doc='rm -r ~/proj/docs'
    alias delete_doccao='rm -r ~/perso/docs'
    alias ssh001='ssh mazars@srv001.astraviz.fr -p 2122'

    # Common command
    alias q='exit'
    alias c='clear'
    alias h='history'
    alias cs='clear;ls'
    alias p='cat'
    alias pd='pwd'
    alias lsa='ls -a'
    alias lsl='ls -l'
    alias pd='pwd'
    alias t='time'
    alias k='kill'
    alias null='/dev/null'

    alias home='cd ~'
    alias root='cd /'
    alias dtop='cd ~/Desktop'
    alias dbox='cd ~/Dropbox'
    alias box='cd ~/Box\ Sync'
    alias gdrive='cd ~/Google\ Drive'
    # Common project directories
    alias cppprojects='cd ~/Dropbox/Projects/C++Projects'
    alias cprojects='cd ~/Dropbox/Projects/CProjects'
    alias pythonprojects='cd ~/Dropbox/Projects/PythonProjects'
    alias goprojects='cd ~/Dropbox/Projects/GoProjects'
    alias rustprojects='cd ~/Dropbox/Projects/RustProjects'
    alias o=open
    alias ..='cd ..'
    alias ...='cd ..; cd ..'
    alias ....='cd ..; cd ..; cd ..'

    alias jupyter="~/.local/bin/jupyter-notebook --no-browser"    

Automatically launch the ssh-agent
============================================

By default, ssh agent is not persistent in WSL (contrary to real linux). A solution is to 
launch automatically the ssh agent at the beginning of the session

.. code::
    
    eval `ssh-agent -s`
    ssh-add .ssh/cao-tri.do@mazars.fr