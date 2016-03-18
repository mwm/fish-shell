[fish](http://fishshell.com/) - the friendly interactive shell [![Build Status](https://travis-ci.org/fish-shell/fish-shell.svg?branch=master)](https://travis-ci.org/fish-shell/fish-shell)
================================================

fish is a smart and user-friendly command line shell for OS X, Linux, and the rest of the family. fish includes features like syntax highlighting, autosuggest-as-you-type, and fancy tab completions that just work, with no configuration required.

For more on fish's design philosophy, see the [design document](http://fishshell.com/docs/current/design.html).

## Quick Start

fish generally works like other shells, like bash or zsh. A few important differences can be found at <http://fishshell.com/docs/current/tutorial.html> by searching for the magic phrase "unlike other shells".

Detailed user documentation is available by running `help` within fish, and also at <http://fishshell.com/docs/current/index.html>

## Building

fish is written in a sane subset of C++98, with a few components from C++TR1. It builds successfully with g++ 4.2 or later, and with clang. It also will build as C++11.

fish can be built using autotools or Xcode. autoconf 2.60 or later is required to build from git versions, but is not required for releases.

fish depends on a curses implementation, such as ncurses. The headers and libraries are required for building.

fish requires PCRE2 due to the regular expression support contained in the `string` builtin. A copy is included with the source code, and will be used automatically if it does not already exist on your system.

fish requires gettext for translation support.

Building the documentation requires Doxygen 1.8.7 or newer.

### Autotools Build

    autoconf [if building from Git]
    ./configure
    make [gmake on BSD]
    sudo make install

### Xcode Development Build

* Build the `base` target in Xcode
* Run the fish executable, for example, in `DerivedData/fish/Build/Products/Debug/base/bin/fish`

### Xcode Build and Install

    xcodebuild install
    sudo ditto /tmp/fish.dst /

## Help, it didn't build!

If fish reports that it could not find curses, try installing a curses development package and build again.

On Debian or Ubuntu you want:

    sudo apt-get install build-essential ncurses-dev libncurses5-dev gettext autoconf

On RedHat, CentOS, or Amazon EC2:

    sudo yum install ncurses-devel

## Testing

The source code for fish includes a large collection of tests. If you are making any changes to fish, running these tests is highly recommended to make sure the behaviour remains consistent.

### Local testing

The tests can be run on your local computer on all operating systems.

Running the tests is only supported from the Autotools build. On OS X, you will require an installation of autoconf; we suggest using [Homebrew](http://brew.sh/) to install these tools.

    autoconf
    ./configure
    make test [gmake on BSD]

### Travis CI Build and Test

The Travis Continuous Integration services can be used to test your changes across multiple platforms. You will need to [fork the fish-shell repository on GitHub](https://help.github.com/articles/fork-a-repo/), or push a copy of the code to your GitHub account.

 1. [Sign in to Travis CI](https://travis-ci.org/auth) with your GitHub account, accepting the GitHub access permissions confirmation.
 2. Once you're signed in, and your repositories are synchronised, go to your [profile page](https://travis-ci.org/profile) and enable the fish-shell repository.
 3. Push your changes to GitHub.

You'll receive an email when the tests are complete telling you whether or not any tests failed.

You'll find the configuration used to control Travis in the `.travis.yml` file.

## Runtime Dependencies

fish requires a curses implementation, such as ncurses, to run.

fish requires PCRE2 due to the regular expression support contained in the `string` builtin. A bundled version will be compiled in automatically at build time if required.

fish requires a number of utilities to operate, which should be present on any Unix, GNU/Linux or OS X system. These include (but are not limited to) hostname, grep, awk, sed, which, and getopt. fish also requires the bc program.

Translation support requires the gettext program.

Some optional features of fish, such as the manual page completion parser and the web configuration tool, require Python.

In order to generate completions from man pages compressed with either lzma or xz, you may need to install an extra Python package. Python versions prior to 2.6 are not supported.  For Python versions 2.6 to 3.2 you need to install the module `backports.lzma`.  How to install it depends on your system and how you installed Python.  Most Linux distributions should include it as a package named `backports-lzma` (or similar).  From version 3.3 onwards, Python already includes the required module.

## Packages for Linux

Instructions on how to find builds for several Linux distros are at <https://github.com/fish-shell/fish-shell/wiki/Nightly-builds>

## Switching to fish

If you wish to use fish as your default shell, use the following command:

	chsh -s /usr/local/bin/fish

chsh will prompt you for your password, and change your default shell. Substitute "/usr/local/bin/fish" with whatever path to fish is in your /etc/shells file.

To switch your default shell back, you can run:

	chsh -s /bin/bash

Substitute /bin/bash with /bin/tcsh or /bin/zsh as appropriate.

## Contact Us

Questions, comments, rants and raves can be posted to the official fish mailing list at <https://lists.sourceforge.net/lists/listinfo/fish-users> or join us on our [gitter.im channel](https://gitter.im/fish-shell/fish-shell) or IRC channel [#fish at irc.oftc.net](https://webchat.oftc.net/?channels=fish). Or use the [fish tag on Stackoverflow](https://stackoverflow.com/questions/tagged/fish).

Found a bug? Have an awesome idea? Please open an issue on this github page.
