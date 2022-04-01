# Setup Microk8s

## 使用 Ansible 作組態管理, 進行自動化安裝 Microk8s

將會自動化執行以下套件

- 安裝 Docker
- 安裝 Microk8s
- 安裝 Helm3

## Ansible guide

Ansible 的安裝手冊及使用方式 [Ansible Guide](https://github.com/ShungYang/ansible).

## Prerequisite

需要先安裝以下 Ansible Roles

- [geerlingguy.docker](https://galaxy.ansible.com/geerlingguy/docker) (2.2.1)
An Ansible Role that installs Docker on Linux.
- [racqspace.microk8s](https://galaxy.ansible.com/racqspace/microk8s) (4.1.3)
Install and configure microk8s - the smallest, simplest, pure production K8s on debian based systems.

## Docker Installation Tasks

- 確認套件尚未安裝於 Managed nodes.
- 確認相依套件已經安裝完成了.
- 確認額外的相依套件已經安裝完成了 (on Ubuntu < 20.04 and any other systems).
- 確認額外的相依套件已經安裝完成了 (on Ubuntu >= 20.04).
- 新增 Docker apt key.
- 新增 Docker apt key (alternative for older systems without SNI).
- 新增 Docker repository 並 Update cache.
- 安裝 Docker, 安裝完後 restart docker.
- 當我們有設定 Option Key-Value 時,確認 /etc/docker/ 目錄存在.
- 將 Option Key-Value 寫入 /etc/docker/daemon.json, 並 restart docker.
- Ensure Docker is started and enabled at boot.
- Install Docker Compose
- Ensure docker users are added to the docker group.

## Microk8s Installation Tasks

- 確認額外的相依套件已經安裝完成了, 並且 Update cache.
- Start and Enable Services.
- Install microk8s
- Wait for microk8s to be ready
- Create kubectl alias
- 新增用戶至 micork8s group
- 為指定用戶新增 .kube 資料夾 ex. /home/osadmin/.kube
- 建立 kubectl config, 內容從 microk8s config 寫入
- reaffirm permission on config directory
- reaffirm permission on config file
- Enable plugin : DNS 指向 MiTac DNS Server

## Helm3 Installation Tasks

- 確認額外的相依套件已經安裝完成了, 並且 Update cache.
- 確認 curl 安裝於 Managed nodes
- 新增 Helm apt key
- 新增 Helm repository, 並 Update cache.
- Install Helm.

**Enjoy!**
