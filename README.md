Neo4j-contrib maven repo
=========================

Using this repo in your maven project
-------------------------------------

* add this to your `pom.xml` for `SNAPSHOTS`

    <repositories>

        <repository>
        
            <id>neo4j-contrib-snapshots</id>
        
            <url>https://github.com/neo4j-contrib/m2/raw/master/snapshots</url>
        
        </repository>
    
    </repositories>


* add this to your `pom.xml` for `RELEASE`

    <repositories>
        <repository>
            <id>neo4j-contrib-release</id>
            <url>https://github.com/neo4j-contrib/m2/raw/master/release</url>
        </repository>
    </repositories>

To deploy to this repo
----------------------

* clone this repo to your machine
    
    git clone 

* add this repo to your pom:

    <distributionManagement>
        <repository>
            <id>repo</id>
            <url>https://github.com/cemerick/cemerick-mvn-repo/raw/master/releases</url>
        </repository>
        <snapshotRepository>
            <id>snapshot-repo</id>
            <url>https://github.com/cemerick/cemerick-mvn-repo/raw/master/snapshots</url>
        </snapshotRepository>
    </distributionManagement>

* deploy your project to your local clone of this repo, e.g.

    mvn -DaltDeploymentRepository=snapshot-repo::default::file:../m2/snapshots clean deploy

* push the added stuff to Github

    cd ../m2
    git add *
    git commit -m "next SNAPSHOT release"
    git push origin master
