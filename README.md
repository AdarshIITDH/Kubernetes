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







