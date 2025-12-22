# Installation

######### Ansible installation steps ##########

######## Master #########

sudo apt update && sudo apt upgrade -y

sudo apt install ansible -y

ansible --version

-- Generate private and public key

ssh-keygen					

chmod 400 /root/pre-key.pem

-- First time login with .pem key

ssh -i /root/pre-key.pem ubuntu@172.31.21.91  	
ssh -i /root/pre-key.pem ubuntu@172.31.21.170

-- Perform steps mentioned in below worker nodes and come back to Master and continue

mkdir ~/ansible-lab && cd ~/ansible-lab

vi inventory

[workers]
node1 ansible_host=172.31.21.91 ansible_user=ubuntu
node2 ansible_host=172.31.21.170 ansible_user=ubuntu

ssh ubuntu@172.31.21.91
ssh ubuntu@172.31.21.170

-- Test:

ansible -i inventory workers -m ping


######## Worker #########

sudo apt update
sudo apt install python3 -y

python3 --version

vi ~/.ssh/authorized_keys

-- Open id_rsa.pub, copy details like below and paste in authorized_keys of worker node and save

example: ssh-ed25519 AAAAC3NzaC1lZDI1NTE5AAAAIBwy+48ceVIsre1Mta70WFX685xWzDAoWh0Umsdn+qGA root@ip-172-31-23-159

chmod 600 ~/.ssh/authorized_keys
chmod 700 ~/.ssh



######### Git installation steps ##########

sudo apt update

sudo apt install git -y

git --version

git config --global user.name "Devendra_Bhoite"

git config --global user.email "dev_bhoite@yahoo.co.in"

git config --list

git config --global init.defaultBranch main

