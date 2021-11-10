# mac-dev-playbook

This is an ansible playbook for setting up a new computer. The original was taken from @geerlinguy's popular [mac-dev-playbook](https://github.com/geerlingguy/mac-dev-playbook) and then modified to suit my own needs.

## Installation

On a fresh mac, install Apple's command line tools.

```console
$ xcode-select --install
```

Then add Python3 and homebrew to the PATH

Install Ansible:

```console
$ export PATH="$HOME/Library/Python/3.8/bin:/opt/homebrew/bin:$PATH"
```

Note: Double check that this path to the Python bin exists. You may have to play with it and explore a little bit.

Then update pip and install ansible

```console
$ sudo -H pip3 install --upgrade pip
...
$ pip3 install ansible
```

Then clone or download this repository to your local drive, install the requirements and run the playbook:

```console
$ ansible-galaxy install -r requirements.yml
...
$ ansible-playbook main.yml --ask-become-pass --ask-vault-pass
...
```

Note: If some Homebrew commands fail, you might need to agree to Xcode's license or fix some other Brew issue. Run brew doctor to see if this is the case.

