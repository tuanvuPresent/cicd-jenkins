# Install docker and docker-compose
```
sudo apt-get update
```
```
sudo apt install docker.io
```
https://docs.docker.com/compose/install/
```
sudo curl -L "https://github.com/docker/compose/releases/download/1.29.2/docker-compose-$(uname -s)-$(uname -m)" -o /usr/local/bin/docker-compose
```
```
sudo chmod +x /usr/local/bin/docker-compose
```

### Create the docker group if it does not exist
```
sudo groupadd docker
```
### Add your user to the docker group.
```
sudo usermod -aG docker $USER
```
```
newgrp docker
```

# Install portainer
```
docker run -d -p 8000:8000 -p 9000:9000 --name=portainer --restart=always -v /var/run/docker.sock:/var/run/docker.sock -v portainer_data:/data portainer/portainer
```
# Install Jenkins

https://hub.docker.com/_/jenkins?tab=description&page=1&ordering=last_updated
```
docker run -d --restart=always -p 8080:8080   -v /var/run/docker.sock:/var/run/docker.sock    -v $(which docker):$(which docker)     -v jenkins_home:/var/jenkins_home  -v  /usr/local/bin/docker-compose:/usr/local/bin/docker-compose    --user 1000:1000  --name jenkins-server jenkins/jenkins:lts
```
### install by docker-compose

```yaml
version: '3.7'
services:
  jenkins:
    image: jenkins/jenkins:lts
    privileged: true
    user: root
    ports:
      - 8080:8080
      - 50000:50000
    container_name: jenkins
    volumes:
      - /jenkins_home:/var/jenkins_home
      - /var/run/docker.sock:/var/run/docker.sock
      - /usr/bin/docker:/usr/bin/docker
      - /usr/local/bin/docker-compose:/usr/local/bin/docker-compose
```

# Create github-Webhooks

Settings ---> Webhooks

### Hướng dẫn setup jenkins
- Get key

![2022-07-02_185607](https://user-images.githubusercontent.com/55792941/176999740-59ab49ac-e1c8-4090-8f46-fc8ab82b0148.jpg)

- Tạo new project 
![2022-07-02_190017](https://user-images.githubusercontent.com/55792941/177000255-4dc33e6c-80a5-46cd-8919-9be2dac5b132.jpg)
- setup repo manager 


![2022-07-02_190216](https://user-images.githubusercontent.com/55792941/177000270-2923286b-49b2-4a13-aa2d-7fc1a8a3d00d.jpg)

![2022-07-02_190451](https://user-images.githubusercontent.com/55792941/177000272-8e6f9da4-91ce-4e42-b00c-9370d9e500da.jpg)


- setup triger
![2022-07-02_190546](https://user-images.githubusercontent.com/55792941/177000287-db823d8f-7d25-407e-b764-b3bfff026626.jpg)





