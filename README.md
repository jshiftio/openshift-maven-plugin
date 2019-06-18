## Openshift Maven Plugin

[![Circle CI](https://circleci.com/gh/jshiftio/openshift-maven-plugin/tree/master.svg?style=shield)](https://circleci.com/gh/jshiftio/openshift-maven-plugin/tree/master)
[![Maintainability Rating](https://sonarcloud.io/api/project_badges/measure?project=jshiftio_openshift-maven-plugin&metric=sqale_rating)](https://sonarcloud.io/dashboard?id=jshiftio_openshift-maven-plugin)
[![Technical Debt](https://sonarcloud.io/api/project_badges/measure?project=jshiftio_openshift-maven-plugin&metric=sqale_index)](https://sonarcloud.io/dashboard?id=jshiftio_openshift-maven-plugin)
[![Coverage](https://sonarcloud.io/api/project_badges/measure?project=jshiftio_openshift-maven-plugin&metric=coverage)](https://sonarcloud.io/dashboard?id=jshiftio_openshift-maven-plugin)

![Sample Demo](oc-maven-plugin-demo.gif)

### Introduction
This Maven plugin is a one-stop-shop for building and deploying Java applications for OpenShift. It brings your Java applications on to OpenShift. It provides a tight integration into maven and benefits from the build configuration already provided. It focuses on three tasks:
+ Building S2I images
+ Creating OpenShift resources
+ Deploy application on OpenShift

### Usage
To enable openshift maven plugin on your project just add this to the plugins sections of your pom.xml:

```
      <plugin>
        <groupId>io.jshift</groupId>
        <artifactId>openshift-maven-plugin</artifactId>
        <version>${jshift.openshift.version}</version>
      </plugin>
```

| Goal                                          | Description                           |
| --------------------------------------------- | ------------------------------------- |
| [`openshift:resource`](https://fabric8io.github.io/fabric8-maven-plugin/#fabric8:resource) | Create OpenShift resource descriptors |
| [`openshift:build`](https://fabric8io.github.io/fabric8-maven-plugin/#fabric8:build) | Build Docker images |
| [`openshift:push`](https://fabric8io.github.io/fabric8-maven-plugin/#fabric8:push) | Push Docker images to a registry  |
| [`openshift:deploy`](https://fabric8io.github.io/fabric8-maven-plugin/#fabric8:deploy) | Deploy OpenShift resource objects to a cluster  |
| [`openshift:watch`](https://fabric8io.github.io/fabric8-maven-plugin/#fabric8:watch) | Watch for doing rebuilds and restarts |

### Features

* Dealing with S2I images and hence inherits its flexible and powerful configuration.
* Supports both OpenShift descriptors
* OpenShift Docker builds with a binary source (as an alternative to a direct image build agains a Docker daemon)
* Various configuration styles:
  * **Zero Configuration** for a quick ramp-up where opinionated defaults will be pre-selected.
  * **Inline Configuration** within the plugin configuration in an XML syntax.
  * **External Configuration** templates of the real deployment descriptors which are enriched by the plugin.
* Flexible customization:
  * **Generators** analyze the Maven build and generated automatic Docker image configurations for certain systems (spring-boot, plain java, karaf ...)
  * **Enrichers** extend the  OpenShift resource descriptors by extra information like SCM labels and can add default objects like Services.
  * Generators and Enrichers can be individually configured and combined into *profiles*

