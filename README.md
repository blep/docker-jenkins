# jenkins
To allow Docker based builds through a Docker running Jenkins Server

```
> docker run --rm -p 8080:8080 -p 4040:4040 -v /var/run/docker.sock:/var/run/docker.sock -v $PWD/jenkins_home:/var/jenkins_home logimethods/jenkins
```

```
> docker run --rm -p 8080:8080 -p 4040:4040 -v /var/run/docker.sock:/var/run/docker.sock -v $PWD/blueocean_home:/var/jenkins_home logimethods/blueocean
```

# Related writeup

http://www.catosplace.net/blog/2015/02/11/running-jenkins-in-docker-containers/
