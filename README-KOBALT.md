
## How to publish custom version

* Compose you own branch from upstream project and local patches
* Change project version in build.gradle : 0.XX-KOBALT1
* Replace repositories config in build.gradle if necessary :

```
def kobaltUserVar = hasProperty("kobaltUser") ? kobaltUser : ""
def kobaltPasswordVar = hasProperty("kobaltPassword") ? kobaltPassword : ""

uploadArchives {
    repositories {
        mavenDeployer {
            repository(url: 'https://nexus.tools.kobalt.fr/repository/kobalt-releases/') {
                authentication(userName: kobaltUserVar, password: kobaltPasswordVar)
            } 
[...]

```
* Tag your version : git tag v0.XX-KOBALTn

* Check that ~/.gradle/gradle.properties configures username and password :

```
kobaltUser=XXXX
kobaltPassword=XXXX
```

* Launch JAVA_HOME=/usr/lib/jvm/java-11-openjdk ./gradlew build uploadArchives

