# my_kali_install_basis
The things I do to Kali when I install it because it's better with that

## VM Hardware
I put 2 CPU with 2 Core each, and 8GB of RAM.

## Configuration
1. In `Settings > Power Manager > Display` deactivate the power management, I don't want the vm to go to sleep
2. Changing the keyboard layout if i'm using an AZERTY keyboard : `sudo dpkg-reconfigure keyboard-configuration` (I choose French (alt.))

## The terminal
1. `sudo apt-get update && sudo apt-get install terminator -y` I like to have Terminator, I also modify the "taskbar" icon to have terminator launched instead of the normal terminal

#### Installing volatility 2 & 3
Let's use pyenv to switch between python 2 & 3
1. `sudo apt install -y build-essential libssl-dev zlib1g-dev libbz2-dev libreadline-dev libsqlite3-dev wget curl llvm libncurses5-dev libncursesw5-dev xz-utils tk-dev libffi-dev liblzma-dev python3-openssl git` Also nice because install a lot of essential tool not present by default like git...
2. `curl https://pyenv.run | bash` dl pyenv
3. Add to the zshrc : 
```bash
echo 'export PYENV_ROOT="$HOME/.pyenv"' >> ~/.zshrc
echo 'export PATH="$PYENV_ROOT/bin:$PATH"' >> ~/.zshrc
echo -e 'if command -v pyenv 1>/dev/null 2>&1; then\n  eval "$(pyenv init --path)"\nfi' >> ~/.zshrc
```
4. `exec $SHELL` reload the shell and check if pyenv is well installed `pyenv`
5. Then install python2 `pyenv install 2.7`
6. to change to python2 : `pyenv global 2` and to go back to python3 : `pyenv global system`
Then let's install [volatility 2](https://github.com/volatilityfoundation/volatility) :
1. `git clone https://github.com/volatilityfoundation/volatility.git` I always clone first to be sure the user can access all files
2. Then I move the tool where I want it `sudo mv volatility /opt/volatility2`
3. I installed all recommanded packages : `pip install distorm3 yara pycrypto pillow openpyxl ujson`
Volatilit3
1. clone : `git clone https://github.com/volatilityfoundation/volatility3.git`
2. move : `sudo mv volatility3 /opt`
3. then install requirements : `cd /opt/volatility3/ && pip install -r requirements.txt` get some error but should be fine

## Essential tools not installed by default
`sudo apt-get install -y ltrace strace ghidra gdb docker.io`

To activate docker : `sudo systemctl enable docker --now`
