# Doozer

## Installing Go

I recommend not using apt, homebrew, or any other packaging system to install
Go. It's better to install straight from source.

Abridged version:

    $ GOROOT=$HOME/src/go # adjust this as you wish
    $ hg clone -r release https://go.googlecode.com/hg/ $GOROOT
    $ cd $GOROOT/src
    $ ./all.bash
    # put the value of $GOROOT/bin in your path

For full details, see <http://golang.org/doc/install.html>.

## Installing Dependencies

You need the `protoc` command
(from <http://code.google.com/p/protobuf/>):

    $ sudo apt-get install protobuf-compiler
    # or
    $ brew install protobuf # (note: I haven't tried this -kr)

Then, install the Go code generation plugin for `protoc`
(<http://code.google.com/p/goprotobuf/>):

    $ goinstall goprotobuf.googlecode.com/hg/proto
    $ cd $GOROOT/src/pkg/goprotobuf.googlecode.com/hg/compiler
    $ make install

If you want to run doozer's tests, install
<http://bmizerany.github.com/roundup/> and run:

    $ goinstall github.com/bmizerany/assert

## Building Doozer

    $ git clone https://github.com/bmizerany/doozer.git
    $ cd doozer/src
    $ ./all.sh

This will build all packages and commands, copy the commands into `$GOBIN`,
and run tests.

## Try It Out

    $ doozerd >/dev/null 2>&1 &
    $ open http://localhost:8080/

This will start up one doozer process and show a web view of its contents.
