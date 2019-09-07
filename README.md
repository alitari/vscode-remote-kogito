# Vscode Remote Development Containers: [Quarkus](https://quarkus.io) [Kogito](https://kogito.kie.org/)

## dev mode

```bash
mvn clean compile quarkus:dev
```

call endpoint with:

```bash
curl -X POST http://localhost:8080/persons \
    -H 'content-type: application/json' \
    -H 'accept: application/json' \
    -d '{"person": {"name":"John Quark", "age": 20}}'
```

## test

```bash
mvn clean test
```

## build and run native executable

```bash
mvn clean package -Pnative
# Find executable in `target` directory.
ls -l target

```

## run integration tests against native executable

```bash
mvn verify -Pnative
```

## build docker image with native executable

```bash
docker build -f src/main/docker/Dockerfile.native -t quarkus/getting-started .
```
