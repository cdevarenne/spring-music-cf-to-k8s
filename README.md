
Notes and instructions to deploy Spring Music example from CloudForundry, containerize and deploy to Kubernetes (k8s) with in-memory SQL H2 Dtabase.

Inbstructions are for Mac OS X and should mostly work on linux except for brew and the like. Will verify on linux when time allows.

## Initial steps to build and deploy

###### Clone repo and build jar

```
git clone https://github.com/cloudfoundry-samples/spring-music.git

./gradlew clean assemble
```

###### Containerize from jar with `pack` CLI

```
brew install buildpacks/tap/pack

pack build sample-app --path samples/apps/java-maven --builder cnbs/sample-builder:bionic
```

###### Run app locally
```
$ java -jar -Dspring.profiles.active=<profile> build/libs/spring-music.jar
```

To run with a specific Spring profile:
```
java -jar -Dspring.profiles.active=<profile> build/libs/spring-music.jar
```

###### Notes and References

Spring Music git repo: https://github.com/cloudfoundry-samples/spring-music
Buildpacks and `pack` cli
https://buildpacks.io/
https://servicebinding.io/


Kf on GP
https://cloud.google.com/migrate/kf/docs/2.11/how-to/spring-music
