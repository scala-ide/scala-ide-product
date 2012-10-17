# Building

The packaged update site location, and the build id need to be configured before running the actual build. This is done using the `configure` profile.

    mvn --non-recursive -Pconfigure -P<build_profile> -Dversion.tag=2.1-M2 process-resources

After that, the _normal_ build can be run

    mvn -P<build_profile> -Dversion.tag=<major.miror-version> -Djarsigner.storepass=******** -Djarsigner.keypass=******** -Djarsigner.keystore=<pathTo/typesafe-keystore/typesafe.keystore> clean package
