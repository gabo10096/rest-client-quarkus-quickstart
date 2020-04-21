# rest-client-quickstart project

### Compilar proyecto en modo native image

```bash
./mvnw clean package -Pnative -Dquarkus.native.container-build=true -Dquarkus.native.container-runtime=docker
```

## Crear imagen Docker 

```bash
docker build -f src/main/docker/Dockerfile.native -t rest-client-quickstart .
```

## Levantar container

```bash
docker run -p 8080:8080 -m 16m --cpus=.25 -d --name rest-client-quickstart rest-client-quickstart
```

## Probar 

```http
GET (http://localhost:8080/country/name/mexico)
```