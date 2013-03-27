This project builds an Eclipse bundle, with the Scala IDE
pre-installed and higher memory settings. This is aimed as a
fast-track to get started with Scala, when people are not experienced
with Eclipse or don't want to install and setup their own IDE.

Besides the Scala IDE, the following software is also pre-installed:

* Scala worksheet
* Java Development Tools
* m2eclipse and m2eclipse-scala

> Note that this project does **not** build the Scala IDE. It packages
> the latest Scala IDE version that has been published in the public,
> stable, update site.

# Building

The packaged update site location, and the build id need to be
configured before running the actual build. This is done using the
`configure` profile.

    mvn --non-recursive -Pconfigure -P<build_profile> -Dversion.tag=<tag> process-resources

After that, the _normal_ build can be run

    mvn -Dtycho.localArtifacts=ignore -P<build_profile> \
        -Dversion.tag=<major.miror-version> -Djarsigner.storepass=******** \
        -Djarsigner.keypass=******** \
        -Djarsigner.keystore=<pathTo/typesafe-keystore/typesafe.keystore> \
        clean package
    
For example, to package using the 2.10 version of the Scala IDE, the
version tag 3.0 tag, run the following two commands:

    $ mvn --non-recursive -Pconfigure -Pscala-2.10.x \
        -Dversion.tag=3.0.0-vfinal process-resources
        
    $ mvn -Dtycho.localArtifacts=ignore -Pscala-2.10.x \
        -Dversion.tag=3.0.0-vfinal -Djarsigner.storepass=******** \
        -Djarsigner.keypass=******** \
        -Djarsigner.keystore=<pathTo/typesafe-keystore/typesafe.keystore> \
        clean package

The resulting products are in
`org.scala-ide.product/target/products/`.  Currently, there are six
platform-dependent archives (Windows, Linux and
Mac, for 32 and 64 bits).


# Issue tracker

You can report issues on the
[Typesfe Stack Assembla space](https://www.assembla.com/spaces/typesafe_stack/tickets),
using the `Packaging` component.

# Contact

This project is maintained by the [Typesafe Scala IDE team](https://wiki.typesafe.com/mediawiki/index.php/Scala_IDE_team).
