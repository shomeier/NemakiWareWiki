English/[日本語](https://github.com/aegif/NemakiWare/wiki/開発(テスト))
***

# OpenCMIS Workbench TCK(Test Compatibility Kit)
OpenCMIS Workbench is CMIS desktop client for developers based on OpenCMIS(Java).  
It provides navigation system, as well as CMIS compliance test tool kit, called TCK(Test Compatibility Kit).  

TCK itself is independent of CMIS Workbench and ```chemistry-opencmis-test-tck-0.13.0.jar``` library exists.  
This library is not written in the format of JUnit and orgranizes tests from CMIS specific test group layers, though they are similar with JUnit, NemakiWare shipped with JUnit wrapper test classes of TCK.  

## How To
- First, start NemakiWare ```core``` application.  
- Then run ```jp.aegif.nemaki.test.tck.tests.AllTests``` as JUnit Test in Eclipse or something.  
- Or ```mvn verify -P product``` in ```core``` directory.  
  Make sure that port 8080 (default) is open, because ```mvn verify``` start/shutdown the server automatically.  

## Setting
- ```src/test/resources.cmis-tck-parameters.properties```
  - specifies CMIS server endpoint to connect.
- ```src/test/resources.cmis-tck-filters.properties```
  - specifies which test or test group to execute in AllTests running by boolean value.

Which tests are going to be done can be controlled with:
- ```src/test/resources.cmis-tck-filters.properties```
- or running directly the test / test group method with @Test annotation in your IDE editor  

## Report
```mvn verify -P product``` execute the tests in maven-surefire-plugin.  
A test report is created under the maven-surefire-plugin default report folder ```target/surefire-reports```.   

## Note
- CMIS TCK, as of version 0.13.0, always fails in VersioningSmokeTest.  
  See [CMIS-935](https://issues.apache.org/jira/browse/CMIS-935).  
  It might be useful to skip VersioningSmokeTest if you are using version 0.13.0, though this bug is already fixed in 0.14.0.  
- Query tests is by default skipped in NemakiWare because the cron intervals and speed of Solr indexing does not catch up with the progress of the test.  
  If you want to test the CMIS query compliance, overwrite ```solr.indexing.force``` to _true_ in ```nemakiware.properties```.  
See [here](https://github.com/aegif/NemakiWare/wiki/Configuration%28Repository%29_-Property).

# Original tests via CMIS protocol
```jp.aegif.nemaki.cmis.original``` package.  
These tests are written as JUnit tests and presuppose the server is running, as much as TCK.  
They are not executed in the usual maven process.  
The purpose is check the behavior of multi-threading, performance etc.  

## MultiThreadTest  
```cmis-original-thread.properties``` specifies the number of objects to be created (= the number of threads of the following operations)  

## JMeter
## How To
- Download JMeter: http://jmeter.apache.org/
- ```sh path/to/apache-jmeter/bin/jmeter.sh```  
- In the menu bar,  _File_ > _Open_ to load a jmx file.  
- Select the test to execute in the left column and click the start button.  