# OSA Event-Based Helloworld Example

## What's OSA?

OSA stands for Open Simulation Architecture.

OSA is primarily intended to be a federating platform for the simulation community: it is designed to favour the integration of new or existing contributions at every level of its architecture.

The platform core supports discrete-event simulation engine(s) built on top of the ObjectWeb Consortium’s Fractal component model: In OSA, the systems to be simulated are modeled and instrumented using Fractal components.

Fractal components offer many advanced and original features, such as multi-programming language support and the ability to share sub-components. In OSA, the event handling is mostly hidden in the controller part of the components, which alleviates noticeably the modeling process, but also ease the replacement of any part of the simulation engine.

Apart the simulation engine, OSA aims at integrating useful tools for modeling, developing, experimenting and analysing simulations.

## OSA Project Modules

OSA is composed of multiples, possibly many, maven sub-projects. However to allow better flexibility, these projects are structurd following a flat structure.

## About this module

This module is an example based on [Fractal's](http://fractal.ow2.org/) hello-world example that demonstrates OSA event-based API: two components are created, one client and one server. The client calls the server's printing service. In the original Fractal example, the printing service simply outputs "Hello world". In our example, when the service is called by the client, an event is scheduled 10 units of time later. This event consists in executing the printing service.

## Usage

WARNING: This demo does NOT work with Java 8. You may want to use a
tool like [jenv](http://www.jenv.be/) to manage multiple java installations.

This module contains an OSA experiment. In order to execute this experiment you need maven (v3.3.1 works fine). 
If you want to try out the released or latest SNAPSHOT release, it should be sufficient to execute the following commands in the current directory (where you found this README):

| Command      | effect               |
| ------------ | -------------------- |   
| `mvn -Prun`  | Run simple example   |
| `mvn -Prun,verbose` |  Run simple example (verbose mode) |
|  `mvn -Prun,multiple`  | Run example with multiple events | 
|  `mvn -Prun,multiple,verbose`  | Run example with multiple events (verbose mode) |
  
  
  Example (notice we use a nexus local maven repository proxy, hence the download from localhost on port 8081):
```
ooo.experiments.newdes.helloworld-event $ mvn -Prun
[INFO] Scanning for projects...
[WARNING] 
[WARNING] Some problems were encountered while building the effective model for org.osadev.osa.experiences.newdes:newdes-helloworld-event:jar:0.8.1-SNAPSHOT
[WARNING] 'parent.relativePath' points at org.osadev.osa.experiments.newdes:osa-expe-newdes instead of org.osadev.osa.experiences.newdes:osa-expe-newdes, please verify your project structure @ line 20, column 10
[WARNING] 
[WARNING] It is highly recommended to fix these problems because they threaten the stability of your build.
[WARNING] 
[WARNING] For this reason, future Maven versions might no longer support building such malformed projects.
[WARNING] 
[INFO]                                                                         
[INFO] ------------------------------------------------------------------------
[INFO] Building OSA event-driven hello-world experiments 0.8.1-SNAPSHOT
[INFO] ------------------------------------------------------------------------
Downloading: http://localhost:8081/nexus/content/groups/public/org/osadev/osa/runtime/newdes/osa-rt-newdes-event-launcher/0.8.1-SNAPSHOT/maven-metadata.xml
Downloading: http://localhost:8081/nexus/content/groups/public/org/osadev/osa/runtime/newdes/osa-newdes-runtime/0.8.1-SNAPSHOT/maven-metadata.xml
Downloading: http://localhost:8081/nexus/content/groups/public/org/osadev/osa/maven-config/0.8.1-SNAPSHOT/maven-metadata.xml
Downloading: http://localhost:8081/nexus/content/groups/public/org/osadev/osa/osa-root/0.8.1-SNAPSHOT/maven-metadata.xml
Downloading: http://localhost:8081/nexus/content/groups/public/org/osadev/osa/simapis/osa-simapis-newdes/0.8.1-SNAPSHOT/maven-metadata.xml
Downloading: http://localhost:8081/nexus/content/groups/public/org/osadev/osa/simapis/osa-simapis/0.8.1-SNAPSHOT/maven-metadata.xml
Downloading: http://localhost:8081/nexus/content/groups/public/org/osadev/osa/engines/osa-engines-newdes/0.8.1-SNAPSHOT/maven-metadata.xml
Downloading: http://localhost:8081/nexus/content/groups/public/org/osadev/osa/engines/osa-engines/0.8.1-SNAPSHOT/maven-metadata.xml
Downloading: http://localhost:8081/nexus/content/groups/public/org/osadev/osa/runtime/newdes/logger/osa-logger-slf4j/0.8.1-SNAPSHOT/maven-metadata.xml
Downloading: http://localhost:8081/nexus/content/groups/public/org/osadev/osa/model/newdes/osa-model-newdes-event-helloworld/0.8.1-SNAPSHOT/maven-metadata.xml
Downloading: http://localhost:8081/nexus/content/groups/public/org/osadev/osa/model/newdes/osa-model-newdes/0.8.1-SNAPSHOT/maven-metadata.xml
Downloading: http://localhost:8081/nexus/content/groups/public/org/osadev/osa/simapis/osa-simapis-newdes-osalet/0.8.1-SNAPSHOT/maven-metadata.xml
[INFO] 
[INFO] --- exec-maven-plugin:1.3.2:exec (default) @ newdes-helloworld-event ---
20: Hello World
-1: Simulation complete.
[INFO] ------------------------------------------------------------------------
[INFO] BUILD SUCCESS
[INFO] ------------------------------------------------------------------------
[INFO] Total time: 3.143s
[INFO] Finished at: Mon Nov 30 16:16:55 CET 2015
[INFO] Final Memory: 9M/156M
[INFO] ------------------------------------------------------------------------
```

If the previous method fails, you can try a full install first (see next section)

## Install

You may want to install all OSA packages from scratch for example if you want to contribute new parts or models, or if the previous execution does not work with just the example module used standalone.

First you need to clone the whole set of OSA sub-modules [from github](http://github.com/osadevs/) in a directory and build everything from scratch. 
All projects can be checked out following a flat multi-module structure (all sub-module lay side by side in a common parent dir) but for the build to work a last step is necessary: due to a bug with a third party dependency, the build must be run from the parent directory in which the pom file from the [release bundle](https://github.com/osadevs/ooo.osa-release-bundle) must be copied or linked. 

On a system with the zsh shell installed this whole procedure can easily be achieved as follows:
```
git clone https://github.com/osadevs/ooo.osa-release-bundle.git
cd ooo.osa-release-bundle
./release.sh -c clone
mvn install
```

This produces the following structure:
```
<install-dir>
  +/ooo.osa-release-bundle/
     +pom.xml
     +relase.sh
     +ooo.engines/
     +ooo.osa-root/
     +ooo.maven-config/
     +ooo.engines.newdes/
     +ooo.model.newdes/
     +ooo.model.newdes.helloworld-event/
     +ooo.model.newdes.helloworld-process/
     +ooo.runtime.newdes/
     +ooo.runtime.newdes.launcher.event/
     +ooo.runtime.newdes.logger/
     +ooo.simapis/
     +ooo.simapis.newdes/
     +ooo.simapis.newdes.osalet/
     +ooo.experiments.newdes/                    
     +ooo.experiments.newdes.helloworld-event/   
     +ooo.experiments.newdes.helloworld-process/
```

If everything works well, the result of the last install command should be as follows:
```
[INFO] ------------------------------------------------------------------------
[INFO] Reactor Summary:
[INFO] 
[INFO] OSA root .......................................... SUCCESS [0.239s]
[INFO] OSA Maven Configuration ........................... SUCCESS [0.409s]
[INFO] OSA Simulation APIs ............................... SUCCESS [0.012s]
[INFO] OSA New Design (newdes) reference API ............. SUCCESS [5.045s]
[INFO] OSA Fractal Annotations (aka Osalet) .............. SUCCESS [0.113s]
[INFO] OSA Common definitions for the newdes runtime ..... SUCCESS [0.011s]
[INFO] OSA Simulation Runtime logger (SLF4J) ............. SUCCESS [0.084s]
[INFO] OSA Simulation Engines ............................ SUCCESS [0.008s]
[INFO] OSA New Design (newdes) API Engine implementation . SUCCESS [3.943s]
[INFO] OSA Runtime Event-Driven Launcher (NewDes) ........ SUCCESS [0.056s]
[INFO] OSA models based on the newdes API and engine ..... SUCCESS [0.352s]
[INFO] OSA event-driven hello-world example model ........ SUCCESS [1.937s]
[INFO] OSA process-oriented hello-world example model .... SUCCESS [1.277s]
[INFO] OSA event-driven hello-world experiments .......... SUCCESS [0.087s]
[INFO] OSA process-oriented hello-world experiments ...... SUCCESS [0.087s]
[INFO] OSA newdes experiences ............................ SUCCESS [0.011s]
[INFO] OSA New Design (newdes) Release Bundle ............ SUCCESS [0.009s]
[INFO] ------------------------------------------------------------------------
[INFO] BUILD SUCCESS
[INFO] ------------------------------------------------------------------------
[INFO] Total time: 14.135s
[INFO] Finished at: Mon Nov 30 17:46:28 CET 2015
[INFO] Final Memory: 41M/522M
[INFO] ------------------------------------------------------------------------
```
