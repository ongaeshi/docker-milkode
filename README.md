# docker-milkode
Milkode's Dockerfile - [Docker Hub](https://hub.docker.com/r/ongaeshi/milkode/)

## Usage

```
$ git clone https://github.com/ongaeshi/docker-milkode.git
$ cd docker-milkode
```

Edit `docker-milode/packages`.

```
https://github.com/ongaeshi/milkode.git
https://github.com/ongaeshi/honyomi.git
.
.
```

Build image.

```
$ docker build -t milkode .
```

Run.

```
$ docker run --name milkode -d -it -p 9292:9292 milkode
```

### Add packages from local files.

Copy source to `docker-milkode/`.

```
aaa/
bbb/
.
.
```

## Credit

Imspired from [nicklegr/docker-milkode](https://github.com/nicklegr/docker-milkode).
