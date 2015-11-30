# OSA SimAPIs module

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

This module contains an OSA experiment. In order to execute this experiment you need maven (v3.3.1 works fine). 
If you want to try out the released or latest SNAPSHOT release, it should be sufficient to execute the following commands in the current directory (where you found this README):

  Command     | effect       
  --------------------------------   
  `mvn -Prun`  | Run simple example
  `mvn -Prun,verbose |  Run simple example (verbose mode)
  `mvn -Prun,multiple`  | Run example with multiple events 
  `mvn -Prun,multiple,verbose`  | Run example with multiple events (verbose mode)
  
  
  Example:
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

