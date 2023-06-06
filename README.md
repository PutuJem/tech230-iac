## What is infrastructure as code?

IaC is the managing and provisioning of instrastructure through code instead of manual processes.

IaC has many benefits for businesses including to cost reduction, eliminate configuration drift and stable & scalable environments.

## Why ansible?

Ansible allows users to quickly and easily deploy multi-tier architecture.

Ansible is agentless and only needs to be installed on the controlled (master node). The systems being controlled do not need to have ansible installed.

![](images/ansible-diagram.webp)

## Section 1: Creating local infrastructure using Ansible and Vagrant

Ensure to have a vagrant configuration file setup in a suitable directory.

> Note: The vagrant file will contain the configuration for the controller, app and db.

Run the virtual machine and check its status.

```bash
vagrant up # Run the virtual machine

vagrant status # Check the status
```

Access the controller through SSH.

```bash
vagrant ssh controller
```

Access the web application through ssh in the controller, a password may also be required.

```bash
ssh vagrant@192.168.33.10 #password: vagrant
```

Update the APT package manager in the web virtual machine and exit back to the controller.

```bash
sudo apt-get update -y
```

Access the database through ssh in the controller, a password may also be required. Repeat the update on the APT package manager and exit back to the controller.

```bash
ssh vagrant@192.168.33.11 #password: vagrant

sudo apt-get update -y

exit
```

To check if you are in the controller, check the ansible version.

```bash
ansible --version
```

In the controller, retrieve all the dependencies common to the environment.

```bash
sudo apt install software-properties-common
```

Add the ansible packages to the APT package manager and install the packages.

```bash
sudo apt-add-repository ppa:ansible/ansible

sudo apt-get update -y
```

Install ansible in the controllers virtual machine.

```bash
sudo apt install ansible
```

Check if the required repository for ansible is now available.

```bash
cd /etc/ansible
```



```bash
sudo apt install tree
```

Look for all the hosts in the agent nodes, inside the posts file and if any found, a ping request is sent.

```bash
sudo ansible all -m ping
```

Within the current directory, access the hosts file and enter the IP address of the web application.

```bash
sudo nano hosts
```