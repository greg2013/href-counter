# href-counter

> A Golang example application which counts internal vs. external hrefs within a page to rate SEO.

The `golang.org/x/net/html` package is used to iterate through all the HTML tokens in the web-page. It provides a working example of parsing HTML piece-by-piece. 

This can be built with the Dockerfile in the repository or through `go get`.

### References

Used in these two blog posts:

* [One-shot containers on Docker Swarm](http://blog.alexellis.io/containers-on-swarm/)
* [Builder pattern vs. Multi-stage builds in Docker](http://blog.alexellis.io/mutli-stage-docker-builds/)

Example:

```
$ url=http://blog.alexellis.io/ go run app.go
{"internal":40,"external":2}

$ url=http://blog.alexellis.io/golang-json-api-client/ go run app.go
{"internal":17,"external":15}
```

# Use docker-compose
```
docker-compose up
docker run --rm -e url=http://www.cnn.com href-counter:1.0
```

# Tips
https://www.digitalocean.com/community/tutorials/how-to-remove-docker-images-containers-and-volumes

## Removing Docker Images
---
Remove dangling images

`docker rmi $(docker images -f dangling=true -q)`

Remove all images

`docker rmi $(docker images -a -q)`

## Removing Containers
---
Run and Remove:

`docker run --rm image_name`

Remove all exited containers

`docker rm $(docker ps -a -f status=exited -q)`


