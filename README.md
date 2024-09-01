# pyenv ubuntu installation
`pyenv` is a tool that helps you manage multiple versions of Python on your system.

How install pyenv on ubuntu

## Update repository
```bash
sudo apt-get update
```

## install compile dependencies
```bash
sudo apt-get install aria2 build-essential curl git libbz2-dev libffi-dev liblzma-dev libncurses5-dev \
libncursesw5-dev libreadline-dev libsqlite3-dev libssl-dev llvm make tk-dev wget xz-utils zlib1g-dev --yes
```
## install pyenv
curl -L https://github.com/pyenv/pyenv-installer/raw/master/bin/pyenv-installer | bash

## add to system config
```bash
if ! grep -Eq "^[#]{4}[[:space:]]pyenv[[:space:]]config$" "${HOME}/.bashrc" ; then echo -e "\n\nsetup pyenv configuration:\nThe following content was inserted at the end of the ${HOME}/.bashrc file\n"; echo -e '\n#### pyenv config\nif [ -f "$HOME/.pyenv/bin/pyenv" ] && ! type -P pyenv &>/dev/null ; then\n  export PYTHON_CONFIGURE_OPTS="--enable-shared"\n  export PYTHON_CFLAGS="-O2"\n  export PYTHON_BUILD_ARIA2_OPTS="-x 10 -k 1M"\n  export PYENV_ROOT="${HOME}/.pyenv"\n  export PATH="${PYENV_ROOT}/bin:${PATH}"\n  eval "$(pyenv init --path)"\n  eval "$(pyenv init -)"\n  eval "$(pyenv virtualenv-init -)"\n  if [[ ! "$(pyenv which python)" == "/usr/bin/python" ]] ; then \n    pyenv virtualenvwrapper_lazy;\n  fi\nfi\n#### pyenv config end' | tee --append "${HOME}/.bashrc"; source "${HOME}/.bashrc"; else  echo -e "\n\npyenv configuration already installed in ${HOME}/.bashrc"; fi
```

## reload .bashrc to run pyenv configurations
```bash
source "${HOME}/.bashrc"
```

## install python version
```bash
pyenv install --skip-existing 3.11
```

## to use in your project
```bash
pyenv local 3.11
```

## to use in your system
```bash
pyenv global 3.11
```

## Reference Docs
https://gist.github.com/luzfcb/1a7f64adf5d12c2d357d0b4319fe9dcd
https://gist.github.com/luzfcb/ef29561ff81e81e348ab7d6824e14404
