# signed-url-generator

[![CI/CD](https://github.com/virtualhealthcitizen/signed-url-generator/actions/workflows/ci-cd.yml/badge.svg)](https://github.com/virtualhealthcitizen/signed-url-generator/actions/workflows/ci-cd.yml)

## Build container

```bash
docker build -t signed-url-generator:1.0.0-SNAPSHOT .
```

## Run container

```bash
GOOGLE_APPLICATION_CREDENTIALS="$1" # Path to your credentials.json file

docker run --rm -p 8080:8080 \
  -e GOOGLE_APPLICATION_CREDENTIALS=${GOOGLE_APPLICATION_CREDENTIALS} \
  -e PORT=8080 \
  -v $HOME/.config/gcloud:/root/.config/gcloud \
  -v $HOME/.m2:/root/.m2 \
  signed-url-generator:1.0.0-SNAPSHOT
```

See [`run_container.sh`](./run_container.sh`).

## Run tests

### Newman

```bash
newman run signed-url-generator.postman_collection.json
```
