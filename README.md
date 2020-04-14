# Gradle Concepts

### Create a Gradle skeleton project with the Gradle Build Init plugin
- Install `gradle`. I used [Homebrew](https://brew.sh/) to do it.
- Create project folder, in this case `gradle-concepts` and `cd` into it.
- Run `gradle init --type java-library`. I selected defaults for all the prompts except: Test Framework I selected JUnit Jupiter, and Source Package I named `org.example`.
- This creates the skeleton of a Java library type project. It also sets up the Gradle wrapper.
- More info: https://docs.gradle.org/current/userguide/build_init_plugin.html

###  Run tests
- Run all tests from command line: `./gradlew test`. This will use the default value of 'test' for system property `platform`
- Run with specifying 'staging' for system property: `./gradlew test -Pplatform=staging`
- The `readProperties()` testcase will fail if you specify the `platform` system property as anything other than 'staging' or 'test'.
- Run a single test case: `./gradlew test --tests org.example.LibraryTest.testAddNumbers`
- From IntelliJ: Create a run configuration for the `test` folder by right-clicking on `src/test` and selecting `Run...`. 

### Miscellaneous Tasks
- Clear gradle cache: `./gradlew --refresh-dependencies`
- Clear gradle cache (brute force): `rm -rf $HOME/.gradle/caches`

### Gradle Properties
- There are a few locations for `gradle.properties` files, see [here](https://docs.gradle.org/current/userguide/build_environment.html#sec:gradle_configuration_properties)
- This example has a `gradle.properties` file in the project root.

### Other Gradle Concepts To Explore
- [ ] Look for best way to pass in passwords etc.
- [ ] Decide on the best place for the config that will reside in a file. The current location of `src/test/resources/config.properties`, or `gradle.properties` or somewhere else? Regardless, some properties will probably have to be passed in via command line or environment varialbe.
- [ ] Add logging?
- [ ] Look into printing a summary of test run: [One option](https://medium.com/@wasyl/pretty-tests-summary-in-gradle-744804dd676c)


### Helpful Links
- [More ways to run only some tests from command line](https://docs.gradle.org/current/userguide/java_testing.html#test_filtering)
- https://linchpiner.github.io/gradle-for-devops-2.html
