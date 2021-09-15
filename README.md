# Install Jenkins

https://hub.docker.com/_/jenkins?tab=description&page=1&ordering=last_updated
```
docker run -d --restart=always -p 8080:8080 -p 50000:50000 -v jenkins_home:/var/jenkins_home jenkins/jenkins:lts-jdk11
docker run -d --restart=always -p 8080:8080  
    -v /var/run/docker.sock:/var/run/docker.sock 
    -v $(which docker):$(which docker) 
    -v jenkins_home:/var/jenkins_home 
    -v  /usr/local/bin/docker-compose:/usr/local/bin/docker-compose
    --user 1000:999 
    --name jenkins-server
    jenkins/jenkins:lts
```

# Create github-Webhooks

Settings ---> Webhooks

### install by docker-compose

```
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
