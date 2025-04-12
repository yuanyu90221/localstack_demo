# localstack_demo

This is repository for localstack_demo

## introduction

```shell
curl -s localhost:4566/_localstack/health | jq
```

## docker info

```yml
services:
  localstack:
    container_name: "${LOCALSTACK_DOCKER_NAME:-localstack_main}"
    image: localstack/localstack
    ports:
      - "127.0.0.1:4566:4566"            # LocalStack Gateway
      - "127.0.0.1:4510-4559:4510-4559"  # external services port range
    environment:
      - DEBUG=${DEBUG:-0}
      - DOCKER_HOST=unix:///var/run/docker.sock
    volumes:
      - "${LOCALSTACK_VOLUME_DIR:-./volume}:/var/lib/localstack"
      - "/var/run/docker.sock:/var/run/docker.sock"
```