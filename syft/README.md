```
docker build -t my-syft .
docker run --rm -v $PWD:/tmp/my-path my-syft docker-archive:/tmp/my-path/alpine.tar > alpine.json
```
