# OpenCMIS Workbench TCK(Test Compatibility Kit)
OpenCMIS Workbench is CMIS desktop client for developers based on OpenCMIS(Java).  
It provides navigation system, as well as CMIS compliance test tool kit, called TCK(Test Compatibility Kit).  

TCK itself is independent of CMIS Workbench and ```chemistry-opencmis-test-tck-0.13.0.jar``` library exists.  
This library is not written in the format of JUnit and orgranizes tests from CMIS specific test group layers, though they are similar with JUnit, NemakiWare shipped with JUnit wrapper test classes of TCK.  

## How To
- First, start NemakiWare ```core``` application.  
- Then run ```jp.aegif.nemaki.test.tck.tests.AllTests``` as JUnit Test in Eclipse or something.  

## Setting
- ```src/test/resources.cmis-tck-parameters.properties```
  - specifies CMIS server endpoint to connect.
- ```src/test/resources.cmis-tck-filters.properties```
  - specifies which test or test group to execute in AllTests running by boolean value.

Test granularity can be modified via:
- ```src/test/resources.cmis-tck-filters.properties```
- running directly the test or test group you wanted to run, which is along with @Test annotation.  

## Note
- CMIS TCK, as of version 0.13.0, always fails in VersioningSmokeTest.  
  See [CMIS-935](https://issues.apache.org/jira/browse/CMIS-935).  
  It might be useful to skip VersioningSmokeTest if you are using version 0.13.0, though this bug is already fixed in 0.14.0.  
- Query tests is by default skipped in NemakiWare because the cron intervals and speed of Solr indexing does not catch up with the progress of the test.  
  If you want to test the CMIS query compliance, overwrite ```solr.indexing.force``` to _true_ in ```nemakiware.properties```.  
See [here](https://github.com/aegif/NemakiWare/wiki/Configuration%28Repository%29_-Property).

# Original tests via CMIS protocol

## Performance test

##

# Unit tests
Now lack of unit tests and the test-driven development are serious issue.  
Baisically CMIS functions and performance can be ensured or measured those above tests, it is urgent to write down unit tests for future enhancement and refactoring.  