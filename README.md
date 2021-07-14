### Getting Lombok and Mapstruct to work in eclipse

1. You need to install lombok into eclipse, see https://projectlombok.org/setup/eclipse
2. Setup your gradle build to allow additional configuration magic to happen (see below)
3. launch eclipse and open the project using the existing gradle project configuration.
4. have the apt-eclipse plugin generate the annotation configuration: run `gradle eclipseJdtApt eclipseFactorypath eclipseJdt` in the terminal.
5. refresh the gradle configuration (right-click --> Gradle --> Refresh Gradle Project)
6. check if the annotation-processing is enabled: right-click the project --> Properties --> java compiler --> annotation processing. Ff not enabled then enable it.
7. clean the project and it should do the trick.

#### Setting up your gradle build to allow additional configuration magic to happen
```
plugins {
    // Apply the java-library plugin for API and implementation separation.
    id 'java-library'
    // Allow configuration calls for setting up the eclipse annotation processing configuration.
    id 'net.ltgt.apt-eclipse' version "0.21"
}
```
