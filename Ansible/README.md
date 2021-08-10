# Ansible

Reinstall ansible or upgrade:
```sh
pip uninstall ansible ansible-base ansible-core
sudo pip uninstall ansible ansible-base ansible-core

curl https://bootstrap.pypa.io/get-pip.py -o get-pip.py
sudo python get-pip.py
sudo python -m pip install ansible
```
Install collection:
```sh
ansible-galaxy collection install community.docker community.general kubernetes.core marmorag.ansodium
```
