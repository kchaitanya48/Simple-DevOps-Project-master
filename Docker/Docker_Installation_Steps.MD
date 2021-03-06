# Installing Docker on Amazon Linux server

### Pre-requisites
1. Amazon Linux EC2 Instance

## Installation Steps

1. Install docker and start docker services
   ```sh 
   yum install docker -y
   docker --version 
   
   # start docker services
   service docker start
   service docker status
   ```
 2.1. verify how many user are in docker unix box
     ->  cat /etc/passwd
        ```
 2.2.   verify existing groups in unix box
     ->   cat /etc/group
        ```
 2.3. Create a user called dockeradmin
      ->   useradd dockeradmin
      ->   passwd dockeradmin
      
 2.4  to know user added into which groups
       -> id dockeradmin

 2.5. add a user to docker group to manage docker 
      -> usermod -aG docker dockeradmin
 2.6. As per above steps, the aws unix box will not allow to login and it will refuse. Below steps have to use to make authentication
      ->  vi /etc/ssh/sshd_config  
      -> /password (this is command for to search password line in sshd_config file.once we open editor then we have to this command to seach in this file)      
      -> service sshd reload( this is command for reload the session. we should not use stop and start here)
      
   
  
       
           
      
   ```
### Validation test
1. Create a tomcat docker container by pulling a docker image from the public docker registry
   ```sh
   docker run -d --name test-tomcat-server -p 8090:8080 tomcat:latest
   ```

## Docker Installation on CentOS server
##### Referance URL : https://docs.docker.com/install/linux/docker-ce/centos/#install-using-the-repository
### Pre-requisites

Please follow below steps to install docker CE on CentoOS server instance. For RedHat only Docker EE available 

1. Install the required packages.

   ```sh 
   sudo yum install -y yum-utils \
   device-mapper-persistent-data \
   lvm2
   ```
  
1. Use the following command to set up the stable repository.
 
   ```sh 
   sudo yum-config-manager \
   --add-repo \
   https://download.docker.com/linux/centos/docker-ce.repo
   ```

### INSTALLING DOCKER CE

1. Install the latest version of Docker CE.
   ```sh 
   sudo yum install docker-ce
   ```

   Note: If prompted to accept the GPG key, verify that the fingerprint matches 
060A 61C5 1B55 8A7F 742B 77AA C52F EB6B 621E 9F35, and if so, accept it.

1. Start Docker.
   ```sh 
   sudo systemctl start docker
   ```

1. Verify that docker is installed correctly by running the hello-world image.
   ```sh
   sudo docker run hello-world
   ```
