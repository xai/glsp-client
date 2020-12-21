# Eclipse GLSP - Client [![build-status](https://img.shields.io/jenkins/build?jobUrl=https%3A%2F%2Fci.eclipse.org%2Fglsp%2Fjob%2Feclipse-glsp%2Fjob%2Fglsp-client%2Fjob%2Fmaster%2F)](https://ci.eclipse.org/glsp/job/eclipse-glsp/job/glsp-client/job/master) [![build-status-server](https://img.shields.io/jenkins/build?jobUrl=https://ci.eclipse.org/glsp/job/deploy-npm-glsp-client/&label=publish)](https://ci.eclipse.org/glsp/job/deploy-npm-glsp-client/)

A web-based diagram client framework for the [Graphical Language Server Platform (GLSP)](https://github.com/eclipse-glsp/glsp) based on [Eclipse Sprotty](https://github.com/eclipse/sprotty).

## Structure
- `@eclipse-glsp/protocol`: Generic client-server communication protocol
- `@eclipse-glsp/client`: sprotty-based GLSP client

## Building
This project is built with `yarn` and is available from npm via [@eclipse-glsp/protocol](https://www.npmjs.com/package/@eclipse-glsp/protocol) and [@eclipse-glsp/client](https://www.npmjs.com/package/@eclipse-glsp/client).

## Workflow Diagram Example
The workflow diagram is a consistent example provided by all GLSP components. The example implements a simple flow chart diagram editor with different types of nodes and edges (see screenshot below). The example can be used to try out different GLSP features, as well as several available integrations with IDE platforms (Theia, VSCode, Eclipse, Standalone).
As the example is fully open source, you can also use it as a blueprint for a custom implementation of a GLSP diagram editor.
See [our project website](https://www.eclipse.org/glsp/documentation/#workflowoverview) for an overview of the workflow example and all components implementing it.

![Workflow Diagram](/documentation/standalone-diagram.gif)

### How to start the Workflow Diagram example?
First, you need to build the glsp-client packages:

```
yarn install
```

Then you need to build and run the Workflow Diagram Server example. Therefore, clone the [`glsp-server`](https://github.com/eclipse-glsp/glsp-server) repository and run the following command in the root of this repository.

    mvn clean verify -Pm2 -Pfatjar

In the folder `glsp-server/examples/org.eclipse.glsp.example.workflow/target`, you should have a jar file `org.eclipse.glsp.example.workflow-X.X.X-SNAPSHOT-glsp.jar` whereas `X.X.X` is the current version. You can now start the server by executing the following commands (make sure you add the parameters `--port=8081 --websocket` as indicated below):

	cd examples/org.eclipse.glsp.example.workflow/target
	java -jar org.eclipse.glsp.example.workflow-X.X.X-SNAPSHOT-glsp.jar org.eclipse.glsp.example.workflow.launch.ExampleServerLauncher --port=8081 --websocket

To start the example server from within your IDE, run the main method of the class [ExampleServerLauncher.java](https://github.com/eclipse-glsp/glsp-server/blob/master/examples/org.eclipse.glsp.example.workflow/src/org/eclipse/glsp/example/workflow/launch/WorkflowServerLauncher.java) in the module `glsp-server/examples/org.eclipse.glsp.example.workflow` with the arguments `--websocket --port=8081` or use the included `Start_Workflow_Example_Server_(Websocket).launch` Launch Configuration for Eclipse.

Once the server is running, open the `glsp-client/examples/workflow-standalone/app/diagram.html` file in your favorite browser.

### Where to find the sources?
In addition to this repository, the source code of the Workflow Diagram server example can be found here: https://github.com/eclipse-glsp/glsp-server/tree/master/examples/org.eclipse.glsp.example.workflow

## More information
For more information, please visit the [Eclipse GLSP Umbrella repository](https://github.com/eclipse-glsp/glsp) and the [Eclipse GLSP Website](https://www.eclipse.org/glsp/). If you have questions, contact us on our [spectrum chat](https://spectrum.chat/glsp/) and have a look at our [communication and support options](https://www.eclipse.org/glsp/contact/).
