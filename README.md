# nodenv-npm-migrate

nodenv-npm-migrate is a [nodenv][] plugin
that provides a `nodenv migrate` command to migrate npm packages from one Node
version to another.

This plugin was forked from
[pyenv-pip-migrate](https://github.com/yyuu/pyenv-pip-migrate).

<!-- toc -->

- [Installation](#installation)
  - [Installing as a nodenv plugin](#installing-as-a-nodenv-plugin)
  - [Installing with Homebrew (for macOS users)](#installing-with-homebrew-for-macos-users)
- [Usage](#usage)
  - [Using `nodenv migrate` with nodenv](#using-nodenv-migrate-with-nodenv)
- [Credits](#credits)

<!-- tocstop -->

## Installation

### Installing as a nodenv plugin

Installing nodenv-npm-migrate as a nodenv plugin will give you access to the
`nodenv migrate` command.

```console
git clone git@github.com:nodenv/nodenv-npm-migrate.git "$(nodenv root)/plugins/nodenv-npm-migrate"
```

This will install the latest development version of nodenv-npm-migrate into
the `$(nodenv root)/plugins/nodenv-npm-migrate` directory. From that directory, you
can check out a specific release tag. To update nodenv-npm-migrate, run `git
pull` to download the latest changes.

### Installing with Homebrew (for macOS users)

MacOS users can install nodenv-npm-migrate with the
[Homebrew](http://brew.sh) package manager.
This will give you access to the `nodenv-migrate` command. If you have nodenv
installed, you will also be able to use the `nodenv migrate` command.

_This is the recommended method of installation if you installed nodenv
with Homebrew._

```console
brew install nodenv/nodenv/nodenv-npm-migrate
```

Or, if you would like to install the latest development release:

```console
brew install --HEAD nodenv/nodenv/nodenv-npm-migrate
```

## Usage

### Using `nodenv migrate` with nodenv

nodenv-npm-migrate uses `npm ls --global --depth=0` to dump all installed
packages in a Node version, and then tries to `npm install` them into another
version.

Let's say if you have following two versions in nodenv.

```console
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
```

To migrate installed packages from `0.12.0` to `iojs-1.6.2`, use `nodenv
migrate`.

```console
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
```

## Credits

Forked from [Yamashita, Yuu's](https://github.com/yyuu)
[pyenv-pip-migrate][] by [Josh Hagins](https://github.com/jawshooah)
and modified for [nodenv][].

[nodenv]: https://github.com/nodenv/nodenv
[pyenv-pip-migrate]: https://github.com/yyuu/pyenv-pip-migrate
