# Vscode Remote Development Containers: [Quarkus](https://quarkus.io) [Kogito](https://kogito.kie.org/)

Devcontainer for using [Quarkus](https://quarkus.io)/[Kogito](https://kogito.kie.org/) with [Infinispan](https://infinispan.org/) for persistence.

## dev mode

```bash
mvn clean compile quarkus:dev
```

open a new terminal and call endpoint with:

```bash
curl -X POST http://localhost:8021/persons \
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
docker build -f src/main/docker/Dockerfile.native -t quarkus/using-kogito .
```

## persistence

In this example non-adults are persisted.

```bash
# persist
curl -X POST http://localhost:8021/persons \
     -H 'content-type: application/json' \
     -H 'accept: application/json' \
     -d '{"person": {"name":"John Quark", "age": 15}}'
# fetch persons
curl -X GET http://localhost:8021/persons \
     -H 'content-type: application/json' \
     -H 'accept: application/json'
```

After restarting the app we get the same result when we fetching persons.
