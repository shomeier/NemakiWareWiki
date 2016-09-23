---

##How to setup eclipse project
You must solve dependencies in advance.  

###Server
Move to `<SOURCE_PATH>/` and
```sh
mvn eclipse:eclipse
```

###Client
Move to `<SOURCE_PATH>/ui` and
```sh
sbt eclipse
```

---

##How to run in developement production

###Server
Move to `<SOURCE_PATH>/` and

```sh
mvn jetty:run
```

###Client
```sh
activator run
```