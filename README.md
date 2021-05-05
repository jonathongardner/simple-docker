Build image:
```sh
docker build with-delete/ -t ghcr.io/jonathongardner/small-docker:with-delete
docker build without-delete/ -t ghcr.io/jonathongardner/small-docker:without-delete
docker build with-source/ -t ghcr.io/jonathongardner/small-docker:with-source
docker build with-source-and-delete/ -t ghcr.io/jonathongardner/small-docker:with-source-and-delete
docker build with-source-no-download/ -t ghcr.io/jonathongardner/small-docker:with-source-no-download
docker build with-gemfile/ -t ghcr.io/jonathongardner/small-docker:with-gemfile
docker build with-gemfile-and-download/ -t ghcr.io/jonathongardner/small-docker:with-gemfile-and-download
docker build with-binary/ -t ghcr.io/jonathongardner/small-docker:with-binary
docker build with-multistep/ -t ghcr.io/jonathongardner/small-docker:with-multistep
```

Save image
```
docker save ghcr.io/jonathongardner/small-docker:with-delete > tars/small-image-with-delete.tar
docker save ghcr.io/jonathongardner/small-docker:without-delete > tars/small-image-without-delete.tar
docker save ghcr.io/jonathongardner/small-docker:with-source > tars/small-image-with-source.tar
docker save ghcr.io/jonathongardner/small-docker:with-source-and-delete > tars/small-image-with-source-and-delete.tar
docker save ghcr.io/jonathongardner/small-docker:with-gemfile > tars/small-image-with-gemfile.tar
docker save ghcr.io/jonathongardner/small-docker:with-gemfile-and-download > tars/small-image-with-gemfile-and-download.tar
docker save ghcr.io/jonathongardner/small-docker:with-source-no-download > tars/small-image-with-source-no-download.tar
docker save ghcr.io/jonathongardner/small-docker:with-binary > tars/small-image-with-binary.tar
docker save ghcr.io/jonathongardner/small-docker:with-multistep > tars/small-image-with-multistep.tar
```

Push to github:
```
docker push ghcr.io/jonathongardner/small-docker:with-delete
docker push ghcr.io/jonathongardner/small-docker:without-delete
docker push ghcr.io/jonathongardner/small-docker:with-source
docker push ghcr.io/jonathongardner/small-docker:with-source-and-delete
docker push ghcr.io/jonathongardner/small-docker:with-gemfile
docker push ghcr.io/jonathongardner/small-docker:with-gemfile-and-download
docker push ghcr.io/jonathongardner/small-docker:with-source-no-download
docker push ghcr.io/jonathongardner/small-docker:with-binary
docker push ghcr.io/jonathongardner/small-docker:with-multistep
```

Trivy
```
docker run --rm -v $HOME/Library/Caches:/root/.cache/ -v $PWD:/tmp aquasec/trivy:0.17.2 image --list-all-pkgs --light -f json -o /tmp/results/tar-with-binary.json --input /tmp/tars/small-image-with-binary.tar
docker run --rm -v $HOME/Library/Caches:/root/.cache/ -v $PWD:/tmp aquasec/trivy:0.17.2 image --list-all-pkgs --light -f json -o /tmp/results/trivy/tar/with-gemfile.json --input /tmp/tars/small-image-with-gemfile.tar
```

Syft
```
docker run --rm -v $PWD:/tmp/my-path anchore/syft:v0.15 -o json docker-archive:/tmp/my-path/tars/small-image-with-delete.tar > results/syft/tar/with-delete.json
```
