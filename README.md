# fuse-ocp-playground

## Quickstarts

This is a collection of quickstarts for Openshift Container Platform.

You need to create a project before starting.


### camel-rest

This is a simple karaf camel route that exposes a ReST endpoint.

## Templates

In the dir templates there are the base templates if you want to manage on openshift the build process

just use:


```
oc create -f templates/karaf2-camel-base-template.json
```

or update exsisting one:

```
oc replace -f templates/karaf2-camel-base-template.json
```


### 


## Speed up the build

set the environment variable in the Builds config:

```
MAVEN_MIRROR_URL=http://host:port/nexus/content/groups/public/
```

eg:

```
MAVEN_MIRROR_URL=http://nexus.ci.svc:8081/nexus/content/groups/public/
```

You can setup a nexus project in Openshift following this [guide](https://docs.openshift.org/latest/dev_guide/app_tutorials/maven_tutorial.html)

