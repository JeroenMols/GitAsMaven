# GitAsMaven
Gradle script to use Git as a private Maven repository.

Currently only BitBucket is supported (because of their free private repositories), but can be easily extended to also support GitHub.

Please find more details in [this blogpost](http://jeroenmols.com/blog/2016/02/05/wagongit/).

## Prerequisites
BitBucket repository with a `releases` as its main branch. Learn how to configure one in [this blogpost](http://jeroenmols.com/blog/2016/02/05/wagongit/).

## Usage
1. Add the following plugin to the top of the `build.gradle` file in your library folder

  ```groovy
  apply from: 'publish-bitbucket.gradle'
  ```

2. Create a `gradle.properties` file within your library folder with the following parameters:

  ```groovy
  ARTIFACT_VERSION=<version_here>
  ARTIFACT_NAME=<libraryname_here>
  ARTIFACT_PACKAGE=<packagename_here>
  ARTIFACT_PACKAGING=aar //You could also use jar

  COMPANY=<bitbucket_team/company_here> //Simply your username if you're not part of a team
  REPOSITORY_NAME=<bitbucket_reponame_here>
  ```

3. Create a `gradle.properties]` file in the root of your project (or better in the global `.gradle` folder on your system) with the following parameters

  ```groovy
  USERNAME=<username_here>
  PASSWORD=<password_here>
  ```
  
  Note: Do not check this file into version control!

4. Run the following command to upload a version to your Maven repository.

  ```bash
  ./gradlew uploadArchives
  ```

## Questions
@molsjeroen
