English/[日本語](https://github.com/aegif/NemakiWare/wiki/%E9%96%8B%E7%99%BA:-%E3%82%A4%E3%83%B3%E3%82%B9%E3%83%88%E3%83%BC%E3%83%A9%E3%81%AE%E3%83%93%E3%83%AB%E3%83%89)
***
# How to
- Execute [make.sh](https://github.com/aegif/NemakiWare/blob/master/setup/installer/make.sh) or [make.bat](https://github.com/aegif/NemakiWare/blob/master/setup/installer/make.bat) in [<SOURCE_PATH>/setup/installer](https://github.com/aegif/NemakiWare/tree/master/setup/installer).
- The script compiles all the stuffs including the files you are developing.
  - For the production environment installer, the files under development can be excluded.
  - To do so, you should add the argument "-p" like `sh make.sh -p `.
- After the script is finished, install.jar will be generated in the same folder.