English/日本語 
***
# How to
- Execute [make.sh](https://github.com/aegif/NemakiWare/blob/master/setup/installer/make.sh) or [make.bat](https://github.com/aegif/NemakiWare/blob/master/setup/installer/make.bat) in [<SOURCE_PATH>/setup/installer](https://github.com/aegif/NemakiWare/tree/master/setup/installer).
- The script compiles all the stuffs including the files you are developing.
  - For the production environment installer, the files under development can be excluded.
  - To do so, you should add the argument "-p" like `sh make.sh -p `.
- After the script is finished, install.jar will be generated in the same folder.