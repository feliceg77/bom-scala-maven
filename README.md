# Create BOM file in sbt project 
Simple overview of how to create a BOM file in sbt/scala projects with SBT and Maven.
BOM file is used by Dependency-Track[Dependency-Track](https://dependencytrack.org/), an intelligent Component Analysis platform that allows organizations to identify and reduce risk in the software supply chain

## How to create a BOM file
Add this line in your build.sbt:
```
pomExtra := <build><plugins><plugin> <groupId>org.cyclonedx</groupId> <artifactId>cyclonedx-maven-plugin</artifactId> <version>2.5.1</version> <executions> <execution> <phase>verify</phase> <goals><goal>makeBom</goal> </goals> </execution> </executions> <configuration> <projectType>library</projectType> <schemaVersion>1.3</schemaVersion> <includeBomSerialNumber>true</includeBomSerialNumber> <includeCompileScope>true</includeCompileScope> <includeProvidedScope>true</includeProvidedScope> <includeRuntimeScope>true</includeRuntimeScope> <includeSystemScope>true</includeSystemScope> <includeTestScope>false</includeTestScope> <includeLicenseText>false</includeLicenseText> <outputFormat>all</outputFormat> <outputName>bom</outputName> </configuration> </plugin></plugins></build>
```

From command line: 
```
sbt makePom
```

Into target folder, find file with ".pom" extension.
Rename file in pom.xml and move it into root of project.

From command line:
```
mvn clean verify
```
Into target folder, find file Bom (xml and json format).
