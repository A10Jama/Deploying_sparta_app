# start by Provisioning the Virtual Machine 
<img width="1208" alt="Screenshot 2023-04-18 at 16 21 26" src="https://user-images.githubusercontent.com/129948378/232824506-421de4a8-dd26-4719-8077-df0f34353ce8.png">

to edit the VagrantFile from the Vagrant Virtualbox connection we add a additional line to sync the app folder to our Vagrant VM. config.vm.synced... is the new line we add.

``` Vagrant.configure("2") do |config|

  config.vm.box = "ubuntu/xenial64"
  config.vm.network "private_network", ip: "192.168.10.100"
  # syncing the app folder
  config.vm.synced_folder "app", "/home/vagrant/app"
end
```
## to ensure nginx is installed 
place these commands in the provision.sh file
```#!/bin/bash
- Update and upgrade system
sudo apt-get update -y
sudo apt-get upgrade -y
- Install Nginx web server
sudo apt-get install nginx -y
- Start Nginx service
sudo service nginx start
```
<img width="971" alt="Screenshot 2023-04-18 at 16 34 29" src="https://user-images.githubusercontent.com/129948378/232829438-03353e58-ca5b-4ee3-bef4-dfa7b8c01db2.png">


# Deploying Sparta App 


### CD into the file with vagrant in it and put in the command 
`" sudo apt-get install python-software-properties"`

<img width="630" alt="Screenshot 2023-04-18 at 14 23 52" src="https://user-images.githubusercontent.com/129948378/232797133-ddf3e021-dd85-4048-a0f8-308dfca0ea59.png">

### when that's finished put in the code 
`" curl -sL https://deb.nodesource.com/setup_6.x | sudo -E bash -"`

<img width="616" alt="Screenshot 2023-04-18 at 14 27 19" src="https://user-images.githubusercontent.com/129948378/232797469-a1dbab3f-7a1d-4c1b-87bd-55fd5543e0bc.png">

### Put in the code 
`"sudo apt-get install nodejs -y"`

<img width="630" alt="Screenshot 2023-04-18 at 14 28 48" src="https://user-images.githubusercontent.com/129948378/232797782-8444e547-7c74-43af-9058-7a6de7534e0a.png">

### Put in the code 
`sudo npm install pm2 -g`

<img width="630" alt="Screenshot 2023-04-18 at 14 29 40" src="https://user-images.githubusercontent.com/129948378/232798012-fa5c34ca-c9d3-4011-a01c-c096f2597990.png">

### Cd into your app then put in the codes 
` "npm install " then put in "npm start"`

<img width="578" alt="Screenshot 2023-04-18 at 14 30 35" src="https://user-images.githubusercontent.com/129948378/232798564-7e46fdda-c1c2-4710-843a-eaafc3f64c96.png">

### Add in 3000 into your nginx web link IP adress 
<img width="715" alt="Screenshot 2023-04-18 at 14 32 41" src="https://user-images.githubusercontent.com/129948378/232798729-5e4b0c65-1945-47f2-bf23-7ff1d09baa0e.png">

### You should see this page when you press enter 
<img width="942" alt="Screenshot 2023-04-18 at 14 04 27" src="https://user-images.githubusercontent.com/129948378/232798973-26f32ef2-130e-41da-af94-b44ae7589164.png">

## To have this already Automated with the provision script add these codes 
<img width="1250" alt="Screenshot 2023-04-18 at 16 05 59" src="https://user-images.githubusercontent.com/129948378/232821475-2b6bbbc2-7cb6-46b6-b0e4-f7fc4ddf558f.png">

```#!/bin/bash

- Update and upgrade system

sudo apt-get update -y

sudo apt-get upgrade -y

- Install Nginx web server

sudo apt-get install nginx -y

- Start Nginx service

sudo service nginx start

- Install Python software properties

sudo apt-get install python-software-properties -y

- Install Node.js and related packages from NodeSource repository

curl -sL https://deb.nodesource.com/setup_6.x | sudo -E bash

sudo apt-get install nodejs -y

- Install pm2 process manager globally

sudo npm install pm2 -g

- Change to app directory

cd app

- Install app dependencies

npm install

- Start app with pm2 process manager

npm start```
