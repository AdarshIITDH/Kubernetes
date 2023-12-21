# Kubernetes
There are multiple ways to set up a Kubernetes cluster on-premise or on a Virtual Machine in the cloud-like EC2.

#### Note: 
Remember, Kubernetes doesn't come pre-equipped with container runtimes or networking components by default. Configuration of Container Runtime Interface (CRI) and Container Network Interface (CNI) is necessary. This step ensures seamless containerization and networking within your Kubernetes cluster.




## 1- Hardway

Will be installing each component with the help of the Kubeadm tool but before that let's have a look at the Architecture first.

![Screenshot 2023-12-15 110700](https://github.com/AdarshIITDH/Kubernetes/assets/60352729/2388eda1-0530-4f65-b359-1372eef5bbb1)

Firstly will be installing the Container run time (CRI), for this demonstration Docker is being used.

### Docker Installation
1. Adding necessary repo
```
curl -fsSL https://download.docker.com/linux/ubuntu/gpg | sudo gpg --dearmor -o /usr/share/keyrings/docker-archive-keyring.gpg
```
2. Adding docker repo
```
echo "deb [arch=amd64 signed-by=/usr/share/keyrings/docker-archive-keyring.gpg] https://download.docker.com/linux/ubuntu $(lsb_release -cs) stable" | sudo tee /etc/apt/sources.list.d/docker.list > /dev/null
```
3. Install necessary dependencies
```
sudo apt-get install apt-transport-https ca-certificates curl gnupg lsb-release -y
```
4. Updating and installing docker
```
sudo apt-get update
sudo apt-get install docker-ce docker-ce-cli containerd.io -y
```
5. Add my user to docker group
```
sudo usermod -aG docker $USER
```
6. Testing the installation
```
sudo docker pull hello-world
```
WOW! CRI is Installed 

### Kubernetes Installation with Kubeadm

To install Kubernetes on your Ubuntu machine, make sure it meets the following requirements:
 - 2 CPUs
 - At least 2GB of RAM
 - At least 2 GB of Disk Space
 - A reliable internet connection
   
Let’s start with the step-by-step process on how to install Kubernetes on Ubuntu.

1. Disabling swap
```
sudo swapoff - a
sudo sed -i '/ swap / s/^/#/' /etc/fstab
```
2. Set up hostnames
We are setting up the hostname of master node and worker node.
```
sudo hostnamectl set-hostname "master-node"
exec bash
```
on worker
```
sudo hostnamectl set-hostname "worker-node1"
```

3. Update the /etc/hosts File for Hostname Resolution

We have to map hostnames to their IP addresses as well. You should update the /etc/hosts file of all nodes(or at least of the master node), as shown below
```
sudo nano /etc/hosts
10.0.0.2 master-node  
10.0.0.3 worker-node1
```











