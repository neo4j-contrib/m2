Neo4j-contrib maven repo
=========================

Using this repo in your maven project
-------------------------------------

* add this to your `pom.xml`:

````xml
    <repositories>
        <repository>
            <id>neo4j-contrib-releases</id>
            <url>https://raw.github.com/neo4j-contrib/m2/master/releases</url>
            <releases>
                <enabled>true</enabled>
            </releases>
            <snapshots>
                <enabled>false</enabled>
            </snapshots>
        </repository>
        <repository>
            <id>neo4j-contrib-snapshots</id>
            <url>https://raw.github.com/neo4j-contrib/m2/master/snapshots</url>
            <releases>
                <enabled>false</enabled>
            </releases>
            <snapshots>
                <enabled>true</enabled>
            </snapshots>
        </repository>
    </repositories>
````

You can remove the releases or snapshots part as needed.

To deploy to this repo
----------------------

* clone this repo to your machine
    
    `git clone`

* add this repo to your pom:

````xml
    <distributionManagement>
        <repository>
            <id>repo</id>
            <url>https://raw.github.com/neo4j-contrib/m2/master/releases</url>
        </repository>
        <snapshotRepository>
            <id>snapshot-repo</id>
            <url>https://raw.github.com/neo4j-contrib/m2/master/snapshots</url>
        </snapshotRepository>
    </distributionManagement>
````

* deploy your project to your local clone of this repo, e.g.

    `mvn -DaltDeploymentRepository=snapshot-repo::default::file:../m2/snapshots clean deploy`
or
    `mvn -DaltDeploymentRepository=repo::default::file:../m2/releases clean deploy`


* push the added stuff to Github

````shell
    cd ../m2
    git add *
    git commit -m "next SNAPSHOT release"
    git push origin master
````
