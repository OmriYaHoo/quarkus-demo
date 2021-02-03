# quarkus-demo project

To run this project you most have a postgres server up and running.

You can change the connection values in the application.properties file.

The best way to do so is to use a container of postgres db. There is a docker-compose file under the resources folder.

Run the following command:
```
docker-compose up -d
```
This will start a postgres server with user/pass - omri/omri. 

## Running the application in dev mode

You can run your application in dev mode that enables live coding using:
```
./mvnw quarkus:dev
```

## Packaging and running the application

The application is packable using `./mvnw package`.
It produces the executable `quarkus-demo-1.0.0-runner.jar` file in `/target` directory.
Be aware that it’s not an _über-jar_ as the dependencies are copied into the `target/lib` directory.

The application is now runnable using `java -jar target/quarkus-demo-1.11.1-runner.jar`.

## Creating a native executable

You will need to have GraalVM installed on your machine, follow this wiki https://quarkus.io/guides/building-native-image#configuring-graalvm each system (Mac, Linux and Windows) requires a different setup.

You can create a native executable using: `./mvnw package -Pnative`.

Or you can use Docker to build the native executable using: `./mvnw package -Pnative -Dquarkus.native.container-build=true`.

You can then execute your binary: `./target/quarkus-demo-1.11.1-runner`

If you want to learn more about building native executables, please consult https://quarkus.io/guides/building-native-image-guide .

## Mac users issues
In case you have issues with running the build for native image try running the commands:  
`xcode-select --install` or `xcode-select --reset` if already installed.  
It's mentioned in the wiki link about GraalVM.