# Jenkins

## Using named volume
To allow Docker based builds through a Docker running Jenkins Server.

Creates a named volume to store Jenkins data (requires Docker 1.9+)

```
docker create -v /var/jenkins_home --name jenkins-data jenkins
```

Then run Jenkins:

```
docker run -d -p 8080:8080 -p 4040:4040 -v /var/run/docker.sock:/var/run/docker.sock  --volumes-from jenkins-data --name myjenkins jenkins
```

To backup Jenkins data:

```
docker run --rm --volumes-from jenkins-data -v $(pwd):/backup ubuntu tar cvf /backup/backup.tar /var/jenkins_home
```

## Using data volumes

Will have access right issues as jenkins user inside the container does not have permission on the host (need to make $PWD/jenkins_home world writable).

```
> docker run --rm -p 8080:8080 -p 4040:4040 -v /var/run/docker.sock:/var/run/docker.sock -v $PWD/jenkins_home:/var/jenkins_home logimethods/jenkins
```

```
> docker run --rm -p 8080:8080 -p 4040:4040 -v /var/run/docker.sock:/var/run/docker.sock -v $PWD/blueocean_home:/var/jenkins_home logimethods/blueocean
```

# Related Article

http://www.catosplace.net/blog/2015/02/11/running-jenkins-in-docker-containers/
https://docs.docker.com/engine/tutorials/dockervolumes/#creating-and-mounting-a-data-volume-container
