#  Ballerina Day: Tooling Tutorial

## Overview

Ballerina tooling currently includes a standalone IDE called Ballerina Composer and also offers IDE plugins for Visual Studio Code and IntelliJ IDEA. 

### Ballerina Composer

Ballerina Composer is the standalone IDE shipped with Ballerina installer. It will get installed alongside Ballerina installation. Please download the specific installer for your platform from [ballerina.io](http://www.ballerina.io/downloads) and install it to get Ballerina Composer up and running. 

To Launch Ballerina Composer after installation,

- Windows : Search for Ballerina Composer in start menu
- Mac: Search for Ballerina Composer in Applications folder
- Linux: Execute ‘composer’ command in the terminal


### IDE plugins

We currently provide plugins for Visual Studio Code and IntelliJ IDEA. To install them, please follow below instructions.

#### Visual Studio Code (VSCode)

* Go to view -> Extensions and search for “Ballerina”
* Plugin details page show in-detail instructions for setting up.
* As explained in plugin description, set ballerina.home config and point it to Ballerina installation director.

#### IntelliJ IDEA (IDEA)

* Go to Preferences -> Plugins and type “Ballerina” in search box. 
* Then click on  “search in repositories”


> Which one should I use?

If you are already familiar with either VSCode or IDEA, we would recommend trying the specific plugin for it. Otherwise, below is a feature comparison between different tools. 

If you are still in doubt, we would recommend using VSCode and the Ballerina plugin for it. Even Though it doesn’t offer all the features available in Ballerina Composer, it offers a simple and lightweight experience with all the mandatory language features, plus a nice preview of the Ballerina Program in sequence diagrams.


Feature | Ballerina Composer | VSCode Plugin | IDEA Plugin
-------- | ---------- | ------------| ------------ 
Basic Language Support (syntax highlighting, diagnostics, refactoring support, etc.) | ✓ | ✓ | ✓ 
Diagram View | ✓ | ✓ | ✗ 
Diagram Editing | ✓ | ✗ | ✗
Debugging | ✓ | ✓ | ✓
TryIt Tool | ✓ | ✗ | ✗
Trace Logs View | ✓ | ✗ | ✗

## How to start writing a program?

Now that you have chosen your IDE, let’s proceed with creation of a project.

* In your terminal, goto the directory you want the project to be created in and execute _ballerina init_ command to create a new Ballerina project. `init` command will create the initial Ballerina project structure as below.

```
project_dir
  ├── Ballerina.toml
```

For more info on structure of Ballerina projects, please refer to [the guide](https://ballerina.io/learn/how-to-structure-ballerina-code/) available in ballerina.io.

* _ballerina init **-i**_ lets you to customize the project generation wizard. It allows you to generate Ballerina service and test skeletons to start with.

* Open the created project in your IDE (This tutorial assumes you are using VSCode) and open *hello_service.bal* file in the editor. This file will by default contain a hello world service created by ballerina init command.


* Lets delete the content in _hello_service.bal_ and create from the scratch while exploring the set of features offered to make development easy.

* You can observe that semantic and syntactic errors are shown (diagnostics) as we type and also observe how the code auto-completion and suggestions are provided according to current scope. 

## Exploring the Intellisense and Diagnostic capabilities

Ballerina Language server is the component which is providing the language smartness to the IDE plugin. Ballerina Language Server supports the following Intellisense capabilities.

### Diagnostics

![Inline Diagnostics in Ballerina LS](/images/diagnostic-inline.png)

![Diagnostics View in Ballerina LS](/images/diagnostic-problems-view.png)

### Completions

![Completions in Ballerina LS](/images/completion-service.png)

![Completions in Ballerina LS](/images/completion-pkg-types.png)

### Refactor support

Code Actions, Rename, Add Imports, Add Documentation, Add Undefined Functions, Code Formatting

![Refactor support in Ballerina LS](/images/code-actions-import.png)

![Refactor support in Ballerina LS](/images/code-actions-create-fn.png)

![Refactor support in Ballerina LS](/images/format-doc.png)

### Go to Definition

![Go to Definition in Ballerina LS](/images/goto-def.png)

### Find References

![Find References in Ballerina LS](/images/find-all-refs.png)

### Signature Help

![Signature Help in Ballerina LS](/images/signature-help.png)

### Hover Support

![Hover Support in Ballerina LS](/images/hover-support.png)

## Testing Ballerina Programs

* Now let’s write a unit test for a Ballerina service.
* Create a new Ballerina Project with the ballerina init -i command.

```
my_project
├── Ballerina.toml
├── hello_service.bal
├── my_package
         ├── hello_service.bal
         ├── tests
                 ├── test_hello_service.bal
```

For more info on testing Ballerina code, please refer to [the guide](https://ballerina.io/learn/how-to-test-ballerina-code/) available in ballerina.io.

## Exploring Ballerina Composer

Now let’s switch over to Ballerina Composer and explore several features it provides.

### Debugging Ballerina Programs

* Open your Ballerina Project in Ballerina Composer (File->Open Project).

* Now add necessary debug points to your source and open the debug panel at left. Click on the Debug option to start debugging your service. 

* Now invoke the service and observe how the debug points are hit and the snapshots of the variables and their values.

![Debugging in Ballerina Composer](/images/debugging.png)

### Design View

* Ballerina has the visual parity for your Ballerina programs. Open your hello_service.bal and click on the design view Icon in composer at the right bottom corner. You can observe how the invocations are shown in a sequence diagrammatic manner.

* You can benefit with the visual editing support, for creating your program skeletons.

* Click on the Edit option on the design view and add definition skeletons from the design view. In the split view, you can see when you add a new construct from the design, respective ballerina source is generated as well.


![Graphical editing in Ballerina Composer](/images/graphical-editing.png)

### Try It

* In the Composer you can invoke your services with the available Try It option. In the debug panel you can find the run option for your Ballerina Programs. 

* Open your hello_service.bal and click on the run item. In the Composer Console, you will be prompted with the Try It. 

* Now let’s click on the Try It and let’s observe how to invoke your service. You can find the available resources in the drop down and select the desired resource and invoke it with the sample data.



![TryIt Tool in Ballerina Composer](/images/try-it-tool.png)

### Trace Logs

* When invoking the services, you can see the Trace Logs for the services through the Trace Log Console at the bottom.

* Invoke the service from Try It and click on the Trace Log option next to Console. You can see the inbound and outbound Trace Logs for your service invocation.

![Trace Logs in Ballerina Composer](/images/trace-logs.png)


## Package Management

Through Ballerina Central (https://central.ballerina.io) you can share your packages with Ballerina Community and pull packages shared by others.

### Setting Up for pushing

* Login to Ballerina Central and create an organization. Now you can get the access token from https://central.ballerina.io/dashboard .
* Get your access token and add this to Settings.toml (<USER_HOME/.ballerina)

### Pushing a package

* Now Let’s publish your package to Ballerina Central.
Go to Your project and open Ballerina.toml and change the org-name config accordingly.
* Now go to your project root and build your package with following Command 
`ballerina build <your_package_name>`
* This will build your package and now you can publish your package to Ballerina Central with the following Command
`ballerina push <your_package_name>`
* Go to Ballerina Central and you can see the published package

### Pulling Packages

* If you need to use an already published package to Ballerina Central, you can pull a package.
* In order to pull a package from central with the following commands
ballerina pull `<org_name>/<package_name>:<version>` (Pull a specific version)
* `ballerina pull <org_name>/<package_name>` (Pull the latest version)

For more info on package management in Ballerina, please refer to [the guide](https://ballerina.io/learn/how-to-publish-packages/) available in ballerina.io.

## API Doc Generation

* You can use the doc generator tool to generate API Docs for your Projects. Ballerina Documentation is part of the Language Syntax itself and Documentation Block Support markdown syntax with some additional tags to refer parameters and attributes.

* Now let’s generate API Docs for your package.
Go to your example project root and enter following command
`ballerina doc <package_name>`

* If you need to generate API Docs for the whole project use the following command
`ballerina doc`

* Now go to the target directory in your project and you can find the generate API Docs under api-docs directory


For more info on documenting Ballerina code, please refer to [the guide](https://ballerina.io/learn/how-to-document-ballerina-code/) available in ballerina.io.

## Swagger / Open API Support

* Ballerina allows you to generate a service stub or a client connector from a swagger or OpenAPI file. 

```
ballerina swagger [mock|client] <swagger_file> 
[-p <packagename> | --package <packagename>]
[-o <path> | --output<path>]
```

* Similarly you can generate a swagger or OpenAPI out from a Ballerina Service Source file.

```
ballerina swagger export <balfile>
[-o <path> | --output <path>]
[-s <servicename> | --service <servicename>]
```

* Ballerina Composer allows you to edit an HTTP Service definition in a swagger view.

