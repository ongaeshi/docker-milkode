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

## Use Data Volume Container

Use it when **you want to persist index data**.

Stop and Remove milkode container.

```
$ docker stop milkode
$ docker rm milkode
```

Create `milkode-data` conatainer and Execute `milk init`

```
$ docker run --name milkode-data -v /root/.milkode busybox
$ docker run --name milkode -d -it -p 9292:9292 --volumes-from milkode-data milkode
$ docker exec milkode milk init
```

Run the command as you like!

```
$ docker exec milkode milk add https://github.com/xxxxx.git
$ docker exec milkode milk add https://github.com/yyyyy.git
$ docker exec milkode milk rm yyyyy
```

Data will remain even after upgrading App.

```
$ docker rm -f milkode
$ docker build -t milkode .
$ docker run --name milkode -d -it -p 9292:9292 --volumes-from milkode-data milkode
```

## Credit

Imspired from [nicklegr/docker-milkode](https://github.com/nicklegr/docker-milkode).
