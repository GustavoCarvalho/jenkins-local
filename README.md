# Set up Jenkins with Docker

### Jenkins pull image
```
$ docker image pull jenkins/jenkins:lts
```

### Jenkins create volume
```
$ docker volume create jenkins
```

### Run the container by attaching the volume and assigning the targeted port. 
```
$ docker container run -d \
    -p [YOUR PORT]:8080 \
    -v [YOUR VOLUME]:/var/jenkins_home \
    --name jenkins-local \
    jenkins/jenkins:lts
```

-d: detached mode
-v: attach volume
-p: assign port target
—name: name of the container


And now, we’re ready to take a look at an example of how you could run this command:
```
$ docker container run -d \
    -p 8080:8080 \
    -v jenkins:/var/jenkins_home \
    --name jenkins-local \
    jenkins/jenkins:lts
```

### See your docker container running
```
$ docker ps -a
```
Copy CONTAINER ID

### Get password
```
$ docker container exec \
    [CONTAINER ID or NAME] \
    sh -c "cat /var/jenkins_home/secrets/initialAdminPassword"
```

### Next steps: Install suggested and create user




