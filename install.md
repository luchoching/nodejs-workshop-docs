# Install

check是否系統有: curl 或 wget

mac:  http://coolestguidesontheplanet.com/install-and-configure-wget-on-os-x/

ubuntu: 

```
sudo apt-get install build-essential libssl-dev
sudo apt-get install curl
```

## NVM

[NVM](https://github.com/creationix/nvm) (Node Version Manager) - Simple bash script to manage multiple active node.js versions

利用nvm來管理node, 有些lib只跑特定版本node

nvm不支援windows, 改使用nvmw, 或是 nvm-widnows, 或是: 
https://www.visualstudio.com/features/node-js-vs

(linux/mac os) install: 

```
curl -o- https://raw.githubusercontent.com/creationix/nvm/v0.29.0/install.sh | bash
wget -qO- https://raw.githubusercontent.com/creationix/nvm/v0.29.0/install.sh | bash
nvm --version
```

then: 

```
nvm install node && nvm alias default node
nvm list
node -v
```

If you want to install a new version of Node.js and migrate npm packages from a previous version:

```
nvm install node --reinstall-packages-from=node
```

移除不用的版本: `nvm uninstall`

## Node.js V4

http://www.cli-nerd.com/2015/09/09/7-reasons-to-upgrade-to-node-v4-now.html

