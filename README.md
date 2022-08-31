
## Build and containerize Spring Music

Build, containerize and run Spring Music example with in-memory SQL H2 Database. WIP.


###### Clone repo and build jar

```
git clone https://github.com/cloudfoundry-samples/spring-music.git

./gradlew clean assemble
```

This will build the example application and create a jar file in : `build/libs`. A 62.5MB jar file in that directory is called `spring-music-1.0.jar` by default.

###### Containerize with `pack` CLI

Set up pack CLI
```
brew install buildpacks/tap/pack
pack builder suggest
pack config default-builder paketobuildpacks/builder:tiny
```

Containerize Spring Music
```
pack build spring-music
```

###### Run Spring Music locally

Run from jar
```
$ java -jar build/libs/spring-music.jar
```

To run with a specific Spring profile:
```
java -jar -Dspring.profiles.active=<profile> build/libs/spring-music.jar
```

Run with docker
```
docker run --rm -p 8080:8080 spring-music
```

Hit the app from a web browser:
```
http://localhost:8080/
```

Spring Boot Actuator endpoints are available at `/actuator`, for example:
```
http://localhost:8080/actuator/health
```

To see all actuator endpoints, try:
```
http://localhost:8080/actuator/mappings
```

###### Notes and References

* Spring Music git repo: https://github.com/cloudfoundry-samples/spring-music
* Buildpacks and `pack` cli: https://buildpacks.io/
* Set up backing services (e.g. db) with: https://servicebinding.io/


Kf on GCP
https://cloud.google.com/migrate/kf/docs/2.11/how-to/spring-music

