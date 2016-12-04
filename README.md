# Install Full DEvelopment environment

1- Install ansible

sudo apt-get install ansible

2- Configure ansible to run on local host

sudo vim /etc/ansible/hosts
"add"
localhost ansible_connection=local

3- Install required ansible roles

sudo ansible-galaxy install -r roles.yml

4- Install all the, jvm, mvn, git, eclipse. please see the full-playbook.yml for details

sudo ansible-playbook full-playbook.yml
 

# Trouble shooting

1- Add the Linuxmint to geerlingguy.git at /etc/ansible/roles
Check you os family: ansible localhost -m setup |grep ansible_os_family

2- fix the following for caarlos0.eclipse
ansible localhost -m setup |grep ansible_distribution
- rename installUbuntu.yml to install_Linuxmint.yml
- change the eclipse download url to the version you want to use
- Add the bndtools plugin to features.yml
- { repo: 'https://dl.bintray.com/bndtools/bndtools/3.1.1/', feature: 'bndtools.main.feature.feature.group'}
- In the main.yml comment out cleanups.yml file
