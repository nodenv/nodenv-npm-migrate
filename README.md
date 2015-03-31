# nodenv-npm-migrate

nodenv-npm-migrate is a [nodenv](https://github.com/OiNutter/nodenv) plugin
that provides a `nodenv migrate` command to migrate npm packages from one Node
version to another.

This plugin was forked from
[pyenv-pip-migrate](https://github.com/yyuu/pyenv-pip-migrate).

## Installation

### Installing as a nodenv plugin

Installing nodenv-npm-migrate as a nodenv plugin will give you access to the
`nodenv migrate` command.

    $ git clone git://github.com/jawshooah/nodenv-npm-migrate.git ~/.nodenv/plugins/nodenv-npm-migrate

This will install the latest development version of nodenv-npm-migrate into
the `~/.nodenv/plugins/nodenv-npm-migrate` directory. From that directory, you
can check out a specific release tag. To update nodenv-npm-migrate, run `git
pull` to download the latest changes.


### Installing with Homebrew (for OS X users)

Mac OS X users can install nodenv-npm-migrate with the
[Homebrew](http://brew.sh) package manager.
This will give you access to the `nodenv-migrate` command. If you have nodenv
installed, you will also be able to use the `nodenv migrate` command.

*This is the recommended method of installation if you installed nodenv
 with Homebrew.*

```
$ brew install jawshooah/nodenv/nodenv-npm-migrate
```

Or, if you would like to install the latest development release:

```
$ brew install --HEAD jawshooah/nodenv/nodenv-npm-migrate
```

## Usage

### Using `nodenv migrate` with nodenv

nodenv-npm-migrate uses `npm ls --global --depth=0` to dump all installed
packages in a Node version, and then tries to `npm install` them into another
version.

Let's say if you have following two versions in nodenv.

    $ nodenv versions
    * 0.12.0 (set by /home/jawshooah/.nodenv/version)
      iojs-1.6.2
    $ npm ls --global --depth=0
    /home/jawshooah/.nodenv/versions/0.12.0/lib
    ├── csslint@0.10.0
    ├── eslint@0.17.1
    ├── git-guilt@0.0.7
    ├── grunt@0.4.5
    ├── grunt-cli@0.1.13
    └── npm@2.7.4

To migrate installed packages from `0.12.0` to `iojs-1.6.2`, use `nodenv
migrate`.

    $ nodenv migrate 0.12.0 iojs-1.6.2
    $ nodenv global iojs-1.6.2
    $ npm ls --global --depth=0
    /home/jawshooah/.nodenv/versions/iojs-1.6.2/lib
    ├── csslint@0.10.0
    ├── eslint@0.17.1
    ├── git-guilt@0.0.7
    ├── grunt@0.4.5
    ├── grunt-cli@0.1.13
    └── npm@2.7.4

### License

(The MIT License)

* Copyright (c) 2015 Joshua Hagins

Permission is hereby granted, free of charge, to any person obtaining
a copy of this software and associated documentation files (the
"Software"), to deal in the Software without restriction, including
without limitation the rights to use, copy, modify, merge, publish,
distribute, sublicense, and/or sell copies of the Software, and to
permit persons to whom the Software is furnished to do so, subject to
the following conditions:

The above copyright notice and this permission notice shall be
included in all copies or substantial portions of the Software.

THE SOFTWARE IS PROVIDED "AS IS", WITHOUT WARRANTY OF ANY KIND,
EXPRESS OR IMPLIED, INCLUDING BUT NOT LIMITED TO THE WARRANTIES OF
MERCHANTABILITY, FITNESS FOR A PARTICULAR PURPOSE AND
NONINFRINGEMENT. IN NO EVENT SHALL THE AUTHORS OR COPYRIGHT HOLDERS BE
LIABLE FOR ANY CLAIM, DAMAGES OR OTHER LIABILITY, WHETHER IN AN ACTION
OF CONTRACT, TORT OR OTHERWISE, ARISING FROM, OUT OF OR IN CONNECTION
WITH THE SOFTWARE OR THE USE OR OTHER DEALINGS IN THE SOFTWARE.
