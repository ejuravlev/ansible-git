# git - ansible role

Ansible role allows to manage git installation state on linux/windows machine

## Usage examples

Simple usage (linux):

```yaml
  - hosts: all
    become: yes
    roles:
      - role: git
```

Git installation with custom system `gitconfig` file:

```yaml
- hosts: all
  roles:
    - role: git
      git_gitconfig_content:
        - 'diff "astextplain"':
            textconv: astextplain
        - http:
            sslBackend: openssl
            sslCAInfo: 'C:/Program Files/Git/mingw64/ssl/certs/ca-bundle.crt'
        - core:
            autocrlf: true
            fscache: true
            symlinks: false
        - pull:
            rebase: false
        - credential:
            helper: manager
        - 'credential "https://dev.azure.com"':
            useHttpPath: true
        - init:
            defaultBranch: master
```

Installation example from binaries:

```yaml
- hosts: all
  roles:
    - role: git
      git_version: 2.8.0
      git_install_from_source: true
```
