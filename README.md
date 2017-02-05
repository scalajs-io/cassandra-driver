Cassandra-driver API for Scala.js
=======================
This is a Scala.js type-safe binding for [cassandra-driver](https://www.npmjs.com/package/cassandra-driver) 

DataStax Node.js Driver for Apache Cassandra.

#### Build Dependencies

* [ScalaJs.io v0.3.x](https://github.com/ldaniels528/scalajs.io)
* [SBT v0.13.13](http://www.scala-sbt.org/download.html)

#### Build/publish the SDK locally

```bash
$ sbt clean publish-local
```

#### Running the tests

Before running the tests the first time, you must ensure the npm packages are installed:

```bash
$ npm install
```

Then you can run the tests:

```bash
$ sbt test
```

#### Examples

```scala
  val client = new Client(new ClientOptions(contactPoints = js.Array("localhost"), keyspace = "classroom"))
  val students = Seq(
    js.Array("123456", "Larry Sanders", "Operating Systems")
  )

  students foreach { params =>
    client.execute("INSERT INTO students (id, name, course) VALUES (?, ?, ?)", params, (err, student) => {
      console.log("student =>", student)
    })
  }
```

#### Artifacts and Resolvers

To add the `cassandra-driver` binding to your project, add the following to your build.sbt:  

```sbt
libraryDependencies += "io.scalajs.npm" %%% "cassandra-driver" % "0.3.0.3"
```

Optionally, you may add the Sonatype Repository resolver:

```sbt   
resolvers += Resolver.sonatypeRepo("releases") 
```