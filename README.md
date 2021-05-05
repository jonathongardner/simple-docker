Build image:
```sh
docker build with-delete/ -t ghcr.io/jonathongardner/small-docker:with-delete
docker build without-delete/ -t ghcr.io/jonathongardner/small-docker:without-delete
docker build with-source/ -t ghcr.io/jonathongardner/small-docker:with-source
docker build with-source-and-delete/ -t ghcr.io/jonathongardner/small-docker:with-source-and-delete
```

Save image
```
docker save ghcr.io/jonathongardner/small-docker:with-delete > tars/small-image-with-delete.tar
docker save ghcr.io/jonathongardner/small-docker:without-delete > tars/small-image-without-delete.tar
docker save ghcr.io/jonathongardner/small-docker:with-source > tars/small-image-with-source.tar
docker save ghcr.io/jonathongardner/small-docker:with-source-and-delete > tars/small-image-with-source-and-delete.tar
```

Push to github:
```
docker push ghcr.io/jonathongardner/small-docker:with-delete
docker push ghcr.io/jonathongardner/small-docker:without-delete
docker push ghcr.io/jonathongardner/small-docker:with-source
docker push ghcr.io/jonathongardner/small-docker:with-source-and-delete
```
