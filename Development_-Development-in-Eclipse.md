English/[日本語](https://github.com/aegif/NemakiWare/wiki/%E9%96%8B%E7%99%BA_-Eclipse%E3%81%A7%E3%81%AE%E9%96%8B%E7%99%BA) 
***
# Project setup
Once the projects' setup is finished, please import them as existing projects into Eclipse.  

## Common
Execute ```mvn install``` in /common folder  

## Core/Solr
Execute ```mvn eclipse:eclipse``` in each project folder(/core, /solr)

## UI
Execute ```activator eclipse``` in the project folder(/ui)

# Application Server
## Core/Solr
They can be run on Jetty by default.  
```mvn jetty:run```  or  
Run from a plugin on Eclipse(ex. [Run Jetty Run](https://code.google.com/p/run-jetty-run/)).  

By default, they are running on port 8080(core), 8983(solr).  

## UI
```activator run``` (By default, port 9000)

# Debug
##UI
When running UI server, execute ```activator -jvm-debug 9999 run```  
Connect to port 9999 by Eclipse's Remote Java Application.