这个代码　在　别人的基础上做的修改，源代码出处：
https://github.com/jashandeep-sohi/nodejs-qnx

实现了：
nodejs 0.10.0　在　QNX650(SP1)上移植

我做的修改：
１．QNX650自带的python是2.5版本，请先把python升级到2.6或者2.7,QNX官方有相关的编译好的bin文件，直接解压即可，有关Python的升级，有问题可以留言交流。  
２．deps/cares/cares.gyp:124行，把  --std=gnu89  改为　-std=gnu89；　否则编译时会报出　参数不识别的错误。  
３．deps/v8/tools/js2c.py中，把有关bz2的　代码屏蔽掉，一共３行，否则会报　无法找到bz2。现在我也没有找到正确导入bz2.so的正确方法，如果有朋友知道，麻烦留言说明一下。  
４．在编译前，最好声明　export LINK=g++　，　否则会报　flock相关的错误；当然，当报出错误以后，再声明，然后继续make也可以。  

在qnx下执行　如下命令：
python2.7 ./configure
make
make install

就可以愉快的使用node了
如有什么问题，请留言交流

/*****英文版******/
My English very pool, I try to translate　Above text
This code Fork Form 
https://github.com/jashandeep-sohi/nodejs-qnx

Achieve：
port nodejs 0.10.1 to QNX650(SP1) successfully

What I change:
1.upgrade your Python version　On QNX  to 2.7
2.change line 124 of deps/cares/cares.gyp, form --std=gnu89  to　-std=gnu89
3.in deps/v8/tools/js2c.py, shield　3 line about bz2
4.export LINK=g++ before make 

under QNX650, commend:
python2.7 ./configure
make
make install

then You can use node joyfully
If you have any question, Please leave comments

/*****英文版******/


Evented I/O for V8 javascript. [![Build Status](https://secure.travis-ci.org/joyent/node.png)](http://travis-ci.org/joyent/node)
===

### To build:

Prerequisites (Unix only):

    * GCC 4.2 or newer
    * Python 2.6 or 2.7
    * GNU Make 3.81 or newer
    * libexecinfo (FreeBSD and OpenBSD only)

Unix/Macintosh:

    ./configure
    make
    make install

If your python binary is in a non-standard location or has a
non-standard name, run the following instead:

    export PYTHON=/path/to/python
    $PYTHON ./configure
    make
    make install

Windows:

    vcbuild.bat

You can download pre-built binaries for various operating systems from
[http://nodejs.org/download/](http://nodejs.org/download/).  The Windows
and OS X installers will prompt you for the location to install to.
The tarballs are self-contained; you can extract them to a local directory
with:

    tar xzf /path/to/node-<version>-<platform>-<arch>.tar.gz

Or system-wide with:

    cd /usr/local && tar --strip-components 1 -xzf \
                         /path/to/node-<version>-<platform>-<arch>.tar.gz

### To run the tests:

Unix/Macintosh:

    make test

Windows:

    vcbuild.bat test

### To build the documentation:

    make doc

### To read the documentation:

    man doc/node.1

Resources for Newcomers
---
  - [The Wiki](https://github.com/joyent/node/wiki)
  - [nodejs.org](http://nodejs.org/)
  - [how to install node.js and npm (node package manager)](http://www.joyent.com/blog/installing-node-and-npm/)
  - [list of modules](https://github.com/joyent/node/wiki/modules)
  - [searching the npm registry](http://npmjs.org/)
  - [list of companies and projects using node](https://github.com/joyent/node/wiki/Projects,-Applications,-and-Companies-Using-Node)
  - [node.js mailing list](http://groups.google.com/group/nodejs)
  - irc chatroom, [#node.js on freenode.net](http://webchat.freenode.net?channels=node.js&uio=d4)
  - [community](https://github.com/joyent/node/wiki/Community)
  - [contributing](https://github.com/joyent/node/wiki/Contributing)
  - [big list of all the helpful wiki pages](https://github.com/joyent/node/wiki/_pages)
