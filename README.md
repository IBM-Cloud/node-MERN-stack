# Create and deploy a cloud native web application using the MERN (MongoDB, Express, React, Node.js) stack

This repository has code to create a web app that is pre-configured with the MERN stack (MongoDB, Express.js, React, Node.js). We use IBM Cloud services to host our application; the IBM Cloud Developer Tools CLI to run and debug locally; and lastly provide native commands to deploy to Kubernetes or Cloud Foundry.

By running this code, you'll understand how to:
* Build an application that uses MongoDB, Express.js, React, and Node.js
* Create an application for monitoring and distributed tracing using App Metrics
* Deploy an application using the IBM Developer Tools CLI or natively with Kubernetes or Cloud Foundry

![](images/architecture.png)

## Flow

1. The user views the React web app with a browser
2. With both components written in Node.js, the React front-end communicates with the Express back-end via RESTful APIs.
3. The back-end Express application uses the Mongo database for storing and retrieving data.
4. Back-end results are communicated back to the the front-end.
5. Front-end results are rendered in a human readable format to the user.

## Included Components

* [IBM Cloud](https://console.bluemix.net/docs/overview/ibm-cloud.html#overview): Provides a computing platform that includes a catalog of cloud services which can be integrated with PaaS and IaaS to build business applications.
* [Kubernetes Cluster](https://console.bluemix.net/docs/containers/container_index.html): Create and manage your own cloud infrastructure and use Kubernetes as your container orchestration engine.
* [MongoDB](https://console.bluemix.net/docs/infrastructure/database-tools/mongodb-topic-description.html#mongodb): Fully featured NoSQL server that is horizontally scalable to meet your enterprise class database service needs.
* [Express](https://expressjs.com/): Most popular and minimalistic web framework for creating API and Web server.
* [React](https://facebook.github.io/react/): JavaScript library for building User Interfaces.

## Featured Technologies

* [Node.js](https://nodejs.org/): An open-source JavaScript run-time environment for executing server-side JavaScript code.
* [Containers](https://www.ibm.com/cloud-computing/bluemix/containers): Virtual software objects that include all the elements that an app needs to run.
* [Cloud Native](https://github.com/cncf): Cloud-native is an approach to building and running applications that exploits the advantages of the cloud computing delivery model

## Getting Started

Ensure [IBM Cloud Developer Tools](https://github.com/IBM-Cloud/ibm-cloud-developer-tools) is installed. To install, run:

```
curl -sL http://ibm.biz/idt-installer | bash
```

> *NOTE:* IDT builds and runs the project using Docker containers, the recommended approach for cloud native development. However, direct use of native tools (e.g. npm) is also supported. See the [Appendix](#APPENDIX.md) for more information.

## Dev mode vs release mode

The starter project supports the concept of dev mode and release mode.  In dev mode, the starter app runs with dev dependencies installed and hot reload enabled for both the frontend and backend aspects of the app.  Dev mode is intended for use during app development. Release mode excludes dev dependencies and runs the app without hot reload. Release mode is intended for running in production.

## Working in Dev Mode 

1. Build the project with all dependencies, including dev dependencies, with the command:

    ```
    idt build --debug
    ```    

    > *NOTE:* Ensure a Docker daemon is running before issuing the above command

2. Run project unit tests with the command:

    ```
    idt test
    ```

3. Run the app in dev mode with command:

    ```
    idt shell run-dev &
    ```

    A web server will runs on port 3000 and the app itself runs on port 3100. The web server and app will automatically reload if changes are made to the source.

4. Run the app in interactive debug mode with command:

    ```
    idt debug
    ```

     The app listens on port 5858 for the debug client to attach to it, and on port 3000 for app requests.

## Working in Release Mode 

1. Build the project:

    ```
    idt build
    ```

    This builds the project using `Dockerfile-tools`. Effectively equivalent to `idt build --debug`.

2. Run the project:

    ```
    idt run
    ```

    This runs the project using the release image built on the fly using `Dockerfile`. Hot reload is not available in the release image.

## Default URLs and sample output

Whether you run in dev mode or release mode, you have the same default URLs available to you:

1. [http://localhost:3000](http://localhost:3000)

2. [http://localhost:3000/appmetrics-dash](http://localhost:3000/appmetrics-dash)

   ![](images/appmetrics.png)

3. [http://localhost:3000/health](http://localhost:3000/health)


## Deployment

These projects are designed for deployment through the IDT CLI to the IBM Cloud, to either Kubernetes (public or private cloud) or Cloud Foundry (public cloud only).

To deploy the app:

```
idt deploy [--target container]
```

Deploys app to Cloud Foundry by default or to Kubernetes (on IBM Cloud) if you specify the --target option.

For deployment to other environments is possible using native commands. See the [Appendix](#APPENDIX.md) for further details.

## Links

* [Node Programming Guide](https://console.bluemix.net/docs/node/index.html#getting-started-tutorial): Tutorial on Node.js app development.
* [Add a Service to Your App](https://console.bluemix.net/docs/apps/reqnsi.html#add_service): Learn how to add a resource to your cloud native app.

## Learn More

* [Other Starter Kits](https://console.bluemix.net/developer/appservice/starter-kits/): Enjoyed this Starter Kit? Check out our other Starter Kits.
* [Architecture Center](https://www.ibm.com/cloud/garage/architectures): Explore Architectures that provide flexible infrastructure solutions.

## License
[Apache 2.0](LICENSE)
