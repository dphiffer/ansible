# ansible

_server caregiving_

## Setup

```
python -m venv env
source env/bin/activate
pip install --upgrade pip
pip install -r requirements.txt
```

## Base install

Each machine has some configuration done prior to ansible touching it.

-   [aarg](setup/aarg.md)

## Running

```
ansible-playbook -i inventory.yml playbook.yml
```
