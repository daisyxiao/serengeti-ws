# serengeti-ws: Serengeti's Web Service and CLI
[Serengeti](http://projectserengeti.org) is an open source project initiated by VMware to enable the rapid deployment of an Apache Hadoop cluster on a virtual platform.

This repository contains the code for the Serengeti Web Service and CLI.

## Getting Started
To jump into using Serengeti, follow our ![Installation Guide] (https://github.com/vmware-serengeti/doc/blob/master/installation_guide_from_source_code.txt). 

## Serengeti Web Service
Serengeti Web Service provides a RESTful API for resources managment and hadoop cluster management running on vSphere.  It works as a proxy to invoke the Serengeti provisioning engine and return fine-grained process execution status to the caller.

### Web Application architecture
![Web service architecture (doc/ws-architecture.png)](https://github.com/vmware-serengeti/serengeti-ws/raw/master/doc/ws-architecture.png "web service architecture")

### REST APIs
<table>
<tr><td>Method</td><td>URL Template</td><td>Request</td><td>Response</td><td>Description</td></tr>
<tr><td>GET</td><td>/hello</td><td>void</td><td>void</td><td></td></tr>
<tr><td>GET</td><td>/tasks</td><td>void</td><td>List of TaskRead</td><td>List all tasks</td></tr>
<tr><td>GET</td><td>/task/{taskId}</td><td>taskId</td><td>TaskRead</td><td>Get task by task id</td></tr>
<tr><td>POST</td><td>/clusters</td><td>ClusterCreate</td><td>Redirect to /task/{taskId}</td><td>Create cluster</td></tr>
<tr><td>GET</td><td>/clusters</td><td>void</td><td>List of ClusterRead</td><td>List all clusters</td></tr>
<tr><td>GET</td><td>/cluster/{clusterName}</td><td>clusterName</td><td>ClusterRead</td><td>Get cluster by name</td></tr>
<tr><td>PUT</td><td>/cluster/{clusterName}</td><td>clusterName; state=start/stop/resume</td><td>Redirect to /task/{taskId}</td><td>Operate a cluster: start; stop or resume a failed creation</td></tr>
<tr><td>PUT</td><td>/cluster/{clusterName}/nodegroup/{groupName}</td><td>clusterName; groupName; instanceNum</td><td>Redirect to /task/{taskId}</td><td>Resize cluster with a new instance number</td></tr>
<tr><td>DELETE</td><td>/cluster/{clusterName}</td><td>clusterName</td><td>Redirect to /task/{taskId}</td><td>Delete a cluster by name</td></tr>
<tr><td>POST</td><td>/resourcepools</td><td>ResourcePoolAdd</td><td>void</td><td>Add a resource pool</td></tr>
<tr><td>GET</td><td>/resourcepools</td><td>void</td><td>List of ResourcePoolRead</td><td>List all resource pools</td></tr>
<tr><td>GET</td><td>/resourcepool/{rpName}</td><td>rpName</td><td>ResourcePoolRead</td><td>Get resource pool by name</td></tr>
<tr><td>DELETE</td><td>/resourcepool/{rpName}</td><td>rpName</td><td>void</td><td>Delete a resource pool by name</td></tr>
<tr><td>POST</td><td>/datastores</td><td>DatastoreAdd</td><td>void</td><td>Add a datastore</td></tr>
<tr><td>GET</td><td>/datastores</td><td>void</td><td>List of DatastoreRead</td><td>List all datastores</td></tr>
<tr><td>GET</td><td>/datastore/{dsName}</td><td>dsName</td><td>DatastoreRead</td><td>Get datastore by name</td></tr>
<tr><td>DELETE</td><td>/datastore/{dsName}</td><td>dsName</td><td>void</td><td>Delete a datastore by name</td></tr>
<tr><td>POST</td><td>/networks</td><td>NetworkAdd</td><td>void</td><td>Add a network</td></tr>
<tr><td>GET</td><td>/networks</td><td>details=true/false</td><td>List of NetworkRead</td><td>List all networks</td></tr>
<tr><td>GET</td><td>/network/{networkName}</td><td>networkName; details=true/false</td><td>NetworkRead</td><td>Get a network by name</td></tr>
<tr><td>DELETE</td><td>/network/{networkName}</td><td>networkName</td><td>void</td><td>Delete a network by name</td></tr>
<tr><td>GET</td><td>/distros</td><td>void</td><td>List of DistroRead</td><td>List all distros</td></tr>
<tr><td>GET</td><td>/distro/{distroName}</td><td>distroName</td><td>DistroRead</td><td>Get a distro by name</td></tr>
</table>

## Serengeti CLI
The CLI is built using the [Spring Shell](https://github.com/SpringSource/spring-shell) project.  The CLI supports an interactive shell mode, a command line mode, and execution of script files.   After compiling, you can find the jar file under cli/target directory.

- Shell mode: java -jar serengeti-cli-0.1.jar. It supports tab key based command hint and completion. It supports history by up/down arrows.

- Command line mode: java -jar serengeti-cli-0.1.jar "command1;command2..."

- Execution of script file: in shell mode or command line mode, execute "script --file scriptFileName". The shell history file named cli.log will help to generate the script file. 

More details can be found at [cli/README.md](https://github.com/vmware-serengeti/serengeti-ws/tree/master/cli). A sample cluster creation specification file can be found at cli/sample.spec.

## Downloading 
You can download a complete Serengeti distribution on [projectserengeti.org](http://projectserengeti.org)  There are no published maven artifacts at this time, stay tuned.

## Documentation
You can find a link to the user guide [here](http://projectserengeti.org).

## Issue Tracking
Serengei's JIRA issue tracker can be found [here](https://issuetracker.springsource.com/browse/SERENGETI)

## Contributing
[Pull requests](http://help.github.com/send-pull-requests) are welcome; see the
[contributor guidelines](https://github.com/vmware-serengeti/serengeti-ws/wiki/Contributor-guidelines).

## Staying in touch
Follow [@VMWserengeti](http://twitter.com/VMWserengeti) on Twitter. You can get help with technical issues, ask questions, and share your experiences with Serengeti on the mailing list [serengeti-user](https://groups.google.com/group/serengeti-user).  To discuss the development of Serengeti sign up on the [serengeti-dev](https://groups.google.com/group/serengeti-dev) mailing list.  

