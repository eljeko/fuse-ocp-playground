# Karaf 2, Camel and REST

This example demonstrates how to use Camel's REST DSL to expose a RESTful API.              

Create the project for the quickstart

```
oc new-project <project_name> --description="<description>" --display-name="<display_name>"
```

eg:
```
oc new-project k2si-camel-rest --description="Karaf camel base s2i template" --display-name="Karaf s2i Camel Rest"
```

### Configuring

The `src/main/fabric8/deployment.yml` could be updated with your custom configs.

### Building

The example can be built with:

    $ mvn install

### Running the example in OpenShift

It is assumed that:
- OpenShift platform is already running, if not you can find details how to [Install OpenShift at your site](https://docs.openshift.com/container-platform/3.3/install_config/index.html).
- Your system is configured for Fabric8 Maven Workflow, if not you can find a [Get Started Guide](https://access.redhat.com/documentation/en/red-hat-jboss-middleware-for-openshift/3/single/red-hat-jboss-fuse-integration-services-20-for-openshift/)
- The Red Hat MySQL xPaaS product should already be installed and running on your OpenShift installation, one simple way to run a MySQL service is following the documentation of the MySQL xPaaS image for OpenShift related to the `mysql-ephemeral` template.

The example can be deployed using a single goal:

    $ mvn fabric8:deploy

This deploys the OpenShift resource descriptors previously generated to the orchestration platform.

When the example runs in OpenShift, you can use the OpenShift client tool to inspect the status, e.g.:

- To list all the running pods:
    ```
    $ oc get pods
    ```

- Then find the name of the pod that runs this quickstart, and output the logs from the running pod with:
    ```
    $ oc logs <name of pod>
    ```

You can also use the OpenShift [Web console](https://docs.openshift.com/container-platform/3.3/getting_started/developers_console.html#developers-console-video) to manage the running pods, view logs and much more.

### Accessing the REST service

Use the script curl-test.sh to post to the endpoint:

(POST) http://karfa-route-karaf.192.168.64.2.nip.io/camel-rest/hello

### Swagger API

The example provides API documentation of the service using Swagger using the _context-path_ `camel-rest-sql/api-doc`. You can access the API documentation from your Web browser at <http://qs-camel-rest-sql.example.com/camel-rest-sql/api-doc>.

### Running via an S2I Application Template

Application templates allow you deploy applications to OpenShift by filling out a form in the OpenShift console that allows you to adjust deployment parameters.  This template uses an S2I source build so that it handle building and deploying the application for you.

First, import the Fuse image streams:

    oc create -f https://raw.githubusercontent.com/jboss-fuse/application-templates/GA/fis-image-streams.json

Then create the quickstart template (included in this repo):

    oc create -f <PATH_TO>/templates/karaf2-camel-base-template.json

Now when you use "Add to Project" button in the OpenShift console, you should see a template for this quickstart. 