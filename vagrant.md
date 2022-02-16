# Vagrant

## vagrant installation

### vagrant requirements
Install virtualbox as a provider
```bash
sudo apt-get update
sudo apt-get install virtualbox
sudo apt-get install virtualbox—ext–pack
```

### Install vagrant
```
curl -fsSL https://apt.releases.hashicorp.com/gpg | sudo apt-key add -
sudo apt-add-repository "deb [arch=amd64] https://apt.releases.hashicorp.com $(lsb_release -cs) main"
sudo apt-get update && sudo apt-get install vagrant
```
