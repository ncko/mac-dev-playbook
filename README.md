# mac-dev-playbook

This is an ansible playbook for setting up a new computer. The original was taken from @geerlinguy's popular [mac-dev-playbook](https://github.com/geerlingguy/mac-dev-playbook) and then modified to suit my own needs.

## Installation

#### Step 1: Install Xcode
On a fresh mac, install Apple's command line tools.

```
xcode-select --install
```

#### Step 2: Add Python3 and homebrew to the PATH

Install Ansible:

```
export PATH="$HOME/Library/Python/3.8/bin:/opt/homebrew/bin:$PATH"
```

> **Note**: Double check that this path to the Python bin exists. You may have to play with it and explore a little bit.

#### Step 3: Update pip

```
sudo -H pip3 install --upgrade pip
```

> **Troubleshoot**: After the previous command, if you receive an error "Cannot import name PackageFinder", the reinstall pip with
> `curl https://bootstrap.pypa.io/get-pip.py -o get-pip.py && python3 get-pip.py`
> then delete the downloaded script with `rm get-pip.py`
> and retry the previous command

#### Step 4: Install Ansible

```
pip3 install ansible
```

Check to see that you have ansible installed in your path

```
ansible --version
```

> **Troubleshoot**: if the response you get indicates that you do not have ansible, rerun the command to update your path (under step 2) and then check again with `ansible --version`

#### Step 5: Clone this repository

```
git clone https://github.com/ncko/mac-dev-playbook
```

#### Step 6: Install the requirements

```
ansible-galaxy install -r requirements.yml
```

#### Step 7: Run the playbook

```
ansible-playbook main.yml --ask-become-pass --ask-vault-pass
```

> **Note**: If some Homebrew commands fail, you might need to agree to Xcode's license or fix some other Brew issue. Run brew doctor to see if this is the case.

