Iustitiacoin Core integration/staging tree
=====================================

What is Iustitiacoin?
----------------

Iustitiacoin is an experimental digital currency that enables instant payments to
anyone, anywhere in the world. Iustitiacoin uses peer-to-peer technology to operate
with no central authority: managing transactions and issuing money are carried
out collectively by the network. Iustitiacoin Core is the name of open source
software which enables the use of this currency.

License
-------

Iustitiacoin Core is released under the terms of the MIT license. See [COPYING](COPYING) for more
information or see https://opensource.org/licenses/MIT.

Development Process
-------------------

The `master` branch is regularly built and tested, but is not guaranteed to be
completely stable. [Tags] are created
regularly to indicate new official, stable release versions of Iustitiacoin Core.

The contribution workflow is described in [CONTRIBUTING.md](CONTRIBUTING.md)
and useful hints for developers can be found in [doc/developer-notes.md](doc/developer-notes.md).

Developer IRC can be found on Freenode at #iustitiacoin-dev.

Testing
-------

Testing and code review is the bottleneck for development; we get more pull
requests than we can review and test on short notice. Please be patient and help out by testing
other people's pull requests, and remember this is a security-critical project where any mistake might cost people
lots of money.

### Automated Testing

Developers are strongly encouraged to write [unit tests](src/test/README.md) for new code, and to
submit new unit tests for old code. Unit tests can be compiled and run
(assuming they weren't disabled in configure) with: `make check`. Further details on running
and extending unit tests can be found in [/src/test/README.md](/src/test/README.md).

There are also [regression and integration tests](/qa) of the RPC interface, written
in Python, that are run automatically on the build server.
These tests can be run (if the [test dependencies](/qa) are installed) with: `qa/pull-tester/rpc-tests.py`

The Travis CI system makes sure that every pull request is built for Windows, Linux, and OS X, and that unit/sanity tests are run automatically.

### Manual Quality Assurance (QA) Testing

Changes should be tested by somebody other than the developer who wrote the
code. This is especially important for large or high-risk changes. It is useful
to add a test plan to the pull request description if testing the changes is
not straightforward.

----------------------------------------------
![Homepage](src/logo.png)

### Installation
Requires Ubuntu 18.04

Preparing The Env

```
sudo apt-get update -y 
sudo apt-get install build-essential -y
sudo apt-get install autoconf libtool pkg-config libboost-all-dev libssl-dev libprotobuf-dev protobuf-compiler libevent-dev libqt4-dev libcanberra-gtk-module libdb++-dev -y 
wget http://download.oracle.com/berkeley-db/db-4.8.30.NC.tar.gz && tar -xvf db-4.8.30.NC.tar.gz && cd db-4.8.30.NC/build_unix && mkdir -p build && BDB_PREFIX=$(pwd)/build && ../dist/configure --disable-shared --enable-cxx --with-pic --prefix=$BDB_PREFIX 
sudo make install

```

#### Compile The Code

```
sudo chmod -R 777 COINFOLDER && cd COINFOLDER 
sudo chmod +x autogen.sh 
./autogen.sh && ./configure CPPFLAGS="-I${BDB_PREFIX}/include/ -O2" LDFLAGS="-L${BDB_PREFIX}/lib/" 
sudo make 
sudo make install
```
