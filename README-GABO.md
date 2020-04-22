# rest-client-quickstart project

### Requisitos

* Java 11 (requerido variable de sistema JAVA_HOME y añadir JAVA_HOME/bin al PATH)
* GraalVM 19.3.1 CE Edition (requerido variable de sistema GRAALVM_HOME y añadir GRAALVM_HOME/bin al PATH)
* Maven 3.6.x (requerido variable de sistema M2_HOME y añadir M2_HOME/bin al PATH)
* Docker

### Compilar proyecto en modo native image

```bash
./mvnw clean package -Pnative -Dquarkus.native.container-build=true -Dquarkus.native.container-runtime=docker
```

### Crear imagen Docker 

```bash
docker build -f src/main/docker/Dockerfile.native -t rest-client-quickstart .
```

### Levantar container

```bash
docker run -p 8080:8080 -m 16m --cpus=.25 -d --name rest-client-quickstart rest-client-quickstart
```

### Probar 

GET: http://localhost:8080/country/name/mexico