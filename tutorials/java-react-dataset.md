```
---
title: US Employment rates Application (Java/Dataset) Tutorial
description: Java Spring application deployed as microservice
---

### Introduction

US Employment rates application is a Java Spring application which is deployed as a microservice.
The example also uses Skaffold which handles the workflow for building, pushing and deploying your application, allowing you to focus on what matters most: writing code.

### Access the application

Click on the Key icon on the dashboard and copy the value under the `DNS` section and `IP` field

URL :  http://##DNS.ip##:30091

### Code Structure

![codestructure](_images/employment-app-structure.png)

It follows a simple modular and MVC pattern. There are 2 folders that are of our interest:
- k8s :  This contains all the deployment and service yaml for the application. This defines the deployment and exposure of our application.
- backend: This contains all the backend code made using Java Spring. The frontend built in React is included in the backend.


### Deploy changes to Kubernetes in Dev Mode

Go to Developer Dashboard tab, it will provide you with the IDE along with the integrated terminal.  Click on the bottom status bar and select `TERMINAL`. 

k8s folder contains all the manifest files and defines the deployment stategy for the application.
One can execute them using :

```execute
kubectl apply -f k8s/
```

In this example , we use `Skaffold` which simplifies local devlopment. You can deploy the application is DEV mode which keeps watching for the files changes and on any change, triggers the entire deployment process automatically without the user having to run and manage it manually.

Navigate to the example:

```execute
cd /home/student/projects/edge-java-react-dataset-deploy
```

```execute
skaffold dev
```

On exiting the command, Skaffold will automatically destroy all the resources it created with above command.


Also, you can use the `skaffold run` to deploy the changes onto kubernetes as a normal mode. In this mode, the resources created remains unless the user deletes them.

### Clean up the Kubernetes resources

You can delete all the application resources created by executing the following command:

```execute
kubectl delete -f k8s/
```
