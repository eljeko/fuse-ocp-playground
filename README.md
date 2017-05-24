# fuse-ocp-playground

## Quickstarts

###

## Templates

In the dir templates there are the base templates if you want to manage on openshift the build process

just use:

```
oc 
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

