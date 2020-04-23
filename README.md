[![CircleCI](https://circleci.com/gh/circleci-orbs-tm/ansible-playbook.svg?style=svg)](https://circleci.com/gh/circleci-orbs-tm/ansible-playbook)
[![](https://github.com/circleci-orbs-tm/ansible-playbook/workflows/Trailing%20whitespace/badge.svg)](https://github.com/circleci-orbs-tm/ansible-playbook/actions?query=workflow%3A%22Trailing+whitespace%22)

# orbss/ansible-playbook

Install Ansible and execure ansible-playbook command in CircleCI job

## Dependencies

None

## Usage

### Register Ansible inventory file

Register Ansible inventory file to CircleCI Environment Variables section. **The data must be registered in base64 format.** The default variable name is NONEXISTENT_ANSIBLE_INVENTORY. The default value must be empty, so **do not register a value with a variable with this name**.

```console
cat inventory

all:
  hosts:
    web:
      ansible_user: ansible
      ansible_host: xxx.xxx.xxx.xxx

cat inventory | base64
YWxsOgogIGhvc3RzOgogICAgd2ViOgogICAgICBhbnNpYmxlX3VzZXI6IGFuc2libGUKICAgICAgYW5zaWJsZV9ob3N0OiB4eHgueHh4Lnh4eC54eHgK
```

![CircleCI add Ansible inventory](https://github.com/circleci-orbs-tm/ansible-playbook/blob/images/images/circleci-add-ansible-inventory.png)


### Register SSH private key

Register SSH private key file to CircleCI Environment Variables section. **The data must be registered in base64 format.** The default variable name is **NONEXISTENT_ANSIBLE_SSH_KEY**. The default value must be empty, so **do not register a value with a variable with this name**.

```console
cat id_rsa

-----BEGIN OPENSSH PRIVATE KEY-----
b3BlbnNzaC1rZXktdjEAAAAABG5vbmUAAAAEbm9uZQAAAAAAAAABAAABFwAAAAdzc2gtcn
NhAAAAAwEAAQAAAQEArPcIv9Yy/N2eAsm3GZGl4DECba/360tcaL4CQfhNGDLClmJTYXfg
5i1+9LDRfrBw3s/zWsCWQA3CcZMcz51wheQWmPRT5SwXIsuK9m5pzlU4gXaVQ0HbkVa1UL
fv3rAGWf4F1YUkbl/jtndW0Hs39u2asSdqpgOt9RfoK6K+voY5z+I7Cm+1TUUr1LXtE07s
NFzA8nQ3kG0UmPYVcJEgjM2YJR2uN+nbtTIOsHdWkV4Dny56eNTr5uWewRLFzlMOmjhOeo
VPgVqaiDb04ILjGmWRDUW5Xircw/1BmTtk54Bwmo4C0U3ctoyPc505iN1xRDCIhIRG2ofz
/2h627HjZwAAA/C9mBdfvZgXXwAAAAdzc2gtcnNhAAABAQCs9wi/1jL83Z4CybcZkaXgMQ
Jtr/frS1xovgJB+E0YMsKWYlNhd+DmLX70sNF+sHDez/NawJZADcJxkxzPnXCF5BaY9FPl
LBciy4r2bmnOVTiBdpVDQduRVrVQt+/esAZZ/gXVhSRuX+O2d1bQezf27ZqxJ2qmA631F+
gror6+hjnP4jsKb7VNRSvUte0TTuw0XMDydDeQbRSY9hVwkSCMzZglHa436du1Mg6wd1aR
XgOfLnp41Ovm5Z7BEsXOUw6aOE56hU+BWpqINvTgguMaZZENRbleKtzD/UGZO2TngHCajg
LRTdy2jI9znTmI3XFEMIiEhEbah/P/aHrbseNnAAAAAwEAAQAAAQANaZKaHagSh7TrDm1O
ZEbynZpMmyqkalGeJa3TI8gGqlkAhFtm4X7lGn4Px25XXqNCA+ohDXIZQXfkir3fM5w4Jb
nC3p9q1AJvRk1eUq2NvHoHQATPFFpMaObifYDyScAUVmhpaEus626jBZoLzKJIWaB3QFE6
0mo46UOtro8QAwPi7N1Ee+x6GJxP3DidQz+5F109FsiWXL4nuVtm2NIBb2vKQ31l6gw/ye
APBtvHRA0reQVpjERdwlaJd4A40818LgFtKNYDDtLBnbJHjNxq0lPF8bvbWu0MtXJEp/E/
6PXX64oj/0sgfaWR/RHE30StqvHesoV+DnCVfq4EL2MRAAAAgQDaJM5bVg1ct7qDwArt0u
hOk6HnUC337gvnXVcmml3exkDAJGbJQEQn7FKl2s+1C4ggzwGozm6rxjOanlf3VEsK2iTp
dWCnV71rFXWAPYyMsg5FyKlGZVNeF0+fEyqEz1sm6dSIJUx6AGAaO4nX79l8eB4i45lzxv
LDF6Cd7oPXwQAAAIEA33zvhtCVn7wT0Y9JeKWqROzQ8v2qGOyMnq47p10ad+VzTZa3+Gzn
QaSuwLb6M3ZW30w7L54EO/cI90WHI3dFkyTQwEoiU5ZNnzG6Vv9FdiQep2Di+yZtThiEOi
0Qu10811CASilFKo1Gvr+6S0cbrj/DnQ6PE4l0KjaDqUXfCaUAAACBAMYgiU/p/+q/lSxO
ds7TNCtXtjPj3OAEoNzbijdCTM44Qb9wgvGqzH320ONWiJTxutqZxDLZHl46rpj8GP+3d4
3Lq5R6OLY0wYf1pTkriMldGlox5ruLHsIrmVHetMrLViYXGzfskij0I8JqNScuqc50k6FU
Fjx0pQjBX/UBQDMbAAAAN21hdHN1bXVyYXRvbW9ub3JpQG1hdHN1bXVyYXRvbW9ub3Jpbm
9NYWNCb29rLXB1cm8ubG9jYWwBAgM=
-----END OPENSSH PRIVATE KEY-----

cat id_rsa | base64
LS0tLS1CRUdJTiBPUEVOU1NIIFBSSVZBVEUgS0VZLS0tLS0KYjNCbGJuTnphQzFyWlhrdGRqRUFBQUFBQkc1dmJtVUFBQUFFYm05dVpRQUFBQUFBQUFBQkFBQUJGd0FBQUFkemMyZ3RjbgpOaEFBQUFBd0VBQVFBQUFRRUFyUGNJdjlZeS9OMmVBc20zR1pHbDRERUNiYS8zNjB0Y2FMNENRZmhOR0RMQ2xtSlRZWGZnCjVpMSs5TERSZnJCdzNzL3pXc0NXUUEzQ2NaTWN6NTF3aGVRV21QUlQ1U3dYSXN1SzltNXB6bFU0Z1hhVlEwSGJrVmExVUwKZnYzckFHV2Y0RjFZVWtibC9qdG5kVzBIczM5dTJhc1NkcXBnT3Q5UmZvSzZLK3ZvWTV6K0k3Q20rMVRVVXIxTFh0RTA3cwpORnpBOG5RM2tHMFVtUFlWY0pFZ2pNMllKUjJ1TituYnRUSU9zSGRXa1Y0RG55NTZlTlRyNXVXZXdSTEZ6bE1PbWpoT2VvClZQZ1ZxYWlEYjA0SUxqR21XUkRVVzVYaXJjdy8xQm1UdGs1NEJ3bW80QzBVM2N0b3lQYzUwNWlOMXhSRENJaElSRzJvZnoKLzJoNjI3SGpad0FBQS9DOW1CZGZ2WmdYWHdBQUFBZHpjMmd0Y25OaEFBQUJBUUNzOXdpLzFqTDgzWjRDeWJjWmthWGdNUQpKdHIvZnJTMXhvdmdKQitFMFlNc0tXWWxOaGQrRG1MWDcwc05GK3NIRGV6L05hd0paQURjSnhreHpQblhDRjVCYVk5RlBsCkxCY2l5NHIyYm1uT1ZUaUJkcFZEUWR1UlZyVlF0Ky9lc0FaWi9nWFZoU1J1WCtPMmQxYlFlemYyN1pxeEoycW1BNjMxRisKZ3JvcjYraGpuUDRqc0tiN1ZOUlN2VXRlMFRUdXcwWE1EeWREZVFiUlNZOWhWd2tTQ016WmdsSGE0MzZkdTFNZzZ3ZDFhUgpYZ09mTG5wNDFPdm01WjdCRXNYT1V3NmFPRTU2aFUrQldwcUlOdlRnZ3VNYVpaRU5SYmxlS3R6RC9VR1pPMlRuZ0hDYWpnCkxSVGR5MmpJOXpuVG1JM1hGRU1JaUVoRWJhaC9QL2FIcmJzZU5uQUFBQUF3RUFBUUFBQVFBTmFaS2FIYWdTaDdUckRtMU8KWkVieW5acE1teXFrYWxHZUphM1RJOGdHcWxrQWhGdG00WDdsR240UHgyNVhYcU5DQStvaERYSVpRWGZraXIzZk01dzRKYgpuQzNwOXExQUp2UmsxZVVxMk52SG9IUUFUUEZGcE1hT2JpZllEeVNjQVVWbWhwYUV1czYyNmpCWm9MektKSVdhQjNRRkU2CjBtbzQ2VU90cm84UUF3UGk3TjFFZSt4NkdKeFAzRGlkUXorNUYxMDlGc2lXWEw0bnVWdG0yTklCYjJ2S1EzMWw2Z3cveWUKQVBCdHZIUkEwcmVRVnBqRVJkd2xhSmQ0QTQwODE4TGdGdEtOWUREdExCbmJKSGpOeHEwbFBGOGJ2Yld1ME10WEpFcC9FLwo2UFhYNjRvai8wc2dmYVdSL1JIRTMwU3Rxdkhlc29WK0RuQ1ZmcTRFTDJNUkFBQUFnUURhSk01YlZnMWN0N3FEd0FydDB1CmhPazZIblVDMzM3Z3ZuWFZjbW1sM2V4a0RBSkdiSlFFUW43RktsMnMrMUM0Z2d6d0dvem02cnhqT2FubGYzVkVzSzJpVHAKZFdDblY3MXJGWFdBUFl5TXNnNUZ5S2xHWlZOZUYwK2ZFeXFFejFzbTZkU0lKVXg2QUdBYU80blg3OWw4ZUI0aTQ1bHp4dgpMREY2Q2Q3b1BYd1FBQUFJRUEzM3p2aHRDVm43d1QwWTlKZUtXcVJPelE4djJxR095TW5xNDdwMTBhZCtWelRaYTMrR3puClFhU3V3TGI2TTNaVzMwdzdMNTRFTy9jSTkwV0hJM2RGa3lUUXdFb2lVNVpObnpHNlZ2OUZkaVFlcDJEaSt5WnRUaGlFT2kKMFF1MTA4MTFDQVNpbEZLbzFHdnIrNlMwY2Jyai9EblE2UEU0bDBLamFEcVVYZkNhVUFBQUNCQU1ZZ2lVL3AvK3EvbFN4TwpkczdUTkN0WHRqUGozT0FFb056YmlqZENUTTQ0UWI5d2d2R3F6SDMyME9OV2lKVHh1dHFaeERMWkhsNDZycGo4R1ArM2Q0CjNMcTVSNk9MWTB3WWYxcFRrcmlNbGRHbG94NXJ1TEhzSXJtVkhldE1yTFZpWVhHemZza2lqMEk4SnFOU2N1cWM1MGs2RlUKRmp4MHBRakJYL1VCUURNYkFBQUFOMjFoZEhOMWJYVnlZWFJ2Ylc5dWIzSnBRRzFoZEhOMWJYVnlZWFJ2Ylc5dWIzSnBibQo5TllXTkNiMjlyTFhCMWNtOHViRzlqWVd3QkFnTT0KLS0tLS1FTkQgT1BFTlNTSCBQUklWQVRFIEtFWS0tLS0tCg==
```

![CircleCI add SSH private key](https://github.com/circleci-orbs-tm/ansible-playbook/blob/images/images/circleci-add-ssh-private-key.png)



### Parameters and commands

See details [CircleCI Orb Registry - orbss/ansible-playbook](https://circleci.com/orbs/registry/orb/orbss/ansible-playbook)

### .circleci/config.yml examples

```yaml
version: 2.1

orbs:
  ansible: orbss/ansible-playbook@0.0.4

executors:
  python:
    docker:
      - image: circleci/python

jobs:
  ansible-playbook:
    executor: python

    parameters:
      version:
        description: |
          Ansible version
        type: string
        default: ''

      galaxy-options:
        description: |
          ansible-galaxy command options
        type: string
        default: ''

      galaxy-requirements-file:
        description: |
          Ansible Galaxy requirements file path
        type: string
        default: ''

      galaxy-roles-path:
        description: |
          ansible-galaxy command roles-path option
        type: string
        default: ''

      inventory:
        description: |
          Ansible inventory file. The default value must be empty,
          so do not store any value to this environment variable.
          The data must be registered in base64 format
        type: env_var_name
        default: NONEXISTENT_ANSIBLE_INVENTORY

      inventory-parameters:
        description: |
          Ansible inventory parameters
        type: string
        default: ''

      playbook:
        description: |
          The path of Ansible playbook
        type: string

      playbook-options:
        description: |
          Ansible-playbook command options
        type: string
        default: ''

      private-key:
        description: |
          SSH private key file. The default value must be empty,
          so do not store any value to this environment variable.
          The data must be registered in base64 format
        type: env_var_name
        default: NONEXISTENT_ANSIBLE_SSH_KEY

    steps:
      - checkout
      - ansible/install:
          version: <<parameters.version>>
      - ansible/galaxy:
          galaxy-options: <<parameters.galaxy-options>>
          galaxy-requirements-file: <<parameters.galaxy-requirements-file>>
          galaxy-roles-path: <<parameters.galaxy-roles-path>>
      - ansible/playbook:
          inventory: <<parameters.inventory>>
          inventory-parameters: <<parameters.inventory-parameters>>
          playbook: <<parameters.playbook>>
          playbook-options: <<parameters.playbook-options>>
          private-key: <<parameters.private-key>>

workflows:
  version: 2
  test-checkout:
    jobs:
      - ansible-playbook:
          galaxy-requirements-file: tests/requirements.yml
          inventory: ANSIBLE_INVENTORY
          inventory-parameters:
          playbook: install.yml
          private-key: ANSIBLE_SSH_KEY
```
