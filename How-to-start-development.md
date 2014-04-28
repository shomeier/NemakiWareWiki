---

##How to setup eclipse project
You must solve dependencies in advance.  
You can use `<SOURCE_PATH>/setup/development/setup.sh(or setup.bat)`, though it's not well tested.

###CMIS server

Move to <SOURCE_PATH>/nemakiware and
```sh
mvn eclipse:eclipse
```

###Search engine
Move to <SOURCE_PATH>/nemakisolr and
```sh
mvn eclipse:eclipse
```

###Client
Move to <SOURCE_PATH>/nemakisolr and
```sh
bundle install
rake db:migrate:reset
```

---

##How to run in developement production
You can use `<SOURCE_PATH>/setup/development/start.sh(or start.bat)` and `<SOURCE_PATH>/setup/development/stop.sh(or stop.bat)`, though they are not well tested.
###CMIS server and search engine
```sh
mvn jetty:run
```

###Client
```sh
rails s
```