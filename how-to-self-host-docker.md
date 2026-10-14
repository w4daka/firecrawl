公式docの手順だとBuildKitがないので

1. docker-buildx プラグインを導入する

```shell
sudo pacman -Sy docker-buildx
```

2. BuildKitを有効にすす

```shell
export DOCKER_BUILDKIT=1
docker buildx ls
```

永続化なら /etc/docker/daemon.json に {"features":{"buildkit":true}} を追記して sudo systemctl restart docker

3. クリーンビルドしなおす。

```shell
docker compose build --no-cache api
docker compose up --build -d
```

self hostの参考については

https://docs.firecrawl.dev/contributing/self-host
