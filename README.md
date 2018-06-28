# How to orchestrate local servers

### 1. bulc start virtualbox servers
```
[just vagrant up 3 servers]

vagrant up
```

### 2. ssh-keygen for each server
```
[ansible_srv]
vagrant ssh ansible_srv
ssh-keygen -t rsa
exit

[mhmt_srv]
vagrant ssh mhmt_srv
ssh-keygen -t rsa
exit

[mhmt_srv2]
vagrant ssh mhmt_srv2
ssh-keygen -t rsa
exit
```

### 3. install ansible in ansible_srv
```shell
sudo yum install -y epel-release
sudo yum install -y ansible vim
```

### 4. try to ansible provisioning
※ At this time, must be **failed**  
because cannot access mhmt server via SSH

```
ansible-playbook -i inventory.txt playbook.yml
```

### 5. manage access right to mhmt servers

```
[ansible_srv]
cat ~/.ssh/id_rsa.pub
ssh-rsa AAAAB3NzaC1yc2EAAAADAQABAAABAQCuSZ51SYsLrXuOBOhXuRPdScr2QV3wbYh89pprxilB0G33EgJ8FWa1S0pAXGA7mEusRG8KeXkCTX0UTISr1It/Pnj5PasZcC4LSWdwfNXepbMxCkMfg3y4xEekAR7p+/P5qVb2bNORm9IQiDaR5x/rBoGltwJjb0imCWYs5BHRw+wYU0GNf2rKiclFrkADdHk/7f1ah0n6i0rfZXPgnsEv8N4V95SK+jlmw0K4wdCcM5syQP9fETTD9f1vQuB/N61AFY+jqRrWv5Lqpj+isUGJfDG2wPEVpKMaDMyF4jitLNvfacxYc6BDaAQJDODPXjg432D0rU5gZ/QMFDzy8JfZ vagrant@herohero

* copy to clipboard

exit

[hmht_srv]
vagrant ssh mhmt_srv
vim ~/.ssh/authorized_keys

* paste clipboard id_rsa.pub of ansible_srv

exit

[hmht_srv2]
vagrant ssh mhmt_srv2
vim ~/.ssh/authorized_keys

* paste clipboard id_rsa.pub of ansible_srv

exit

```
### 6. reprovision ansible in ansible_srv
※ this time should be successfully done

```
ansible-playbook -i inventory.txt playbook.yml
```

### 7. check package installed or not

```
[mhmt_srv]
vagrant ssh mhmt_srv
php -v

PHP 5.4.16 (cli) (built: Apr 12 2018 19:02:01)
Copyright (c) 1997-2013 The PHP Group
Zend Engine v2.4.0, Copyright (c) 1998-2013 Zend Technologies

exit

[mhmt_srv2]
vagrant ssh mhmt_srv2
php -v

PHP 5.4.16 (cli) (built: Apr 12 2018 19:02:01)
Copyright (c) 1997-2013 The PHP Group
Zend Engine v2.4.0, Copyright (c) 1998-2013 Zend Technologies
```

Congratulations
