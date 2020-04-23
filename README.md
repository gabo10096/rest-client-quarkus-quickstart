# rest-client-quarkus-example

## Prerequisites

You will need:

* Java 11+ installed
* Environment variable JAVA_HOME set accordingly
* Maven 3.6.2+ installed
* Docker

When using native image compilation, you will also need:

* GraalVM 19.3.1 installed
* Environment variable GRAALVM_HOME set accordingly

Note that GraalVM native image compilation typically requires other packages (glibc-devel, zlib-devel and gcc) to be installed too. You also need 'native-image' installed in GraalVM (using 'gu install native-image'). Please refer to GraalVM installation documentation for more details.



## Containerize the application using Docker

##### Generate the native executable for the Docker image

```bash
mvn clean package -Pnative -Dquarkus.native.container-build=true -Dquarkus.native.container-runtime=docker
```

##### Generate the Docker image 

```bash
docker build -f src/main/docker/Dockerfile.native -t rest-client-quickstart .
```

##### Generate the container

```bash
docker run -p 8080:8080 -m 16m --cpus=.25 -d --name rest-client-quickstart rest-client-quickstart
```



## Testing 

##### Example Usage

Once the service is up and running, you can use the following example to interact with the service.

GET: http://localhost:8080/country/name/mexico

###### Curl command

```bash
curl "http://localhost:8080/country/name/mexico" -H "accept: application/json"
```

##### Example response:

```json
[
    {
        "alpha2Code": "MX",
        "capital": "Mexico City",
        "currencies": [
            {
                "code": "MXN",
                "name": "Mexican peso",
                "symbol": "$"
            }   
        ],
        "name": "Mexico"
    }
]
```