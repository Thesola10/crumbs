# Crumbs

Crumbs is a command-line utility for the shell, for storing commands under a meaningful name in a hierarchy

## Motivation

For web service tests I am used to sending a lot of HTTP Requests via `curl`. The command line invocation can be quite complex and long and I wanted to be able to organize them in a directory like structure. Also I wanted to have a context sensitive auto completion for the different command invocations.

## Why not use aliases?

Aliases do not allow a user to use foward slashes in the alias name in order to create complex hierarchies and therefore no context sensitive auto completion.

## Installation

### Arch Linux AUR package

For installing crumbs on Arch Linux an AUR package is provided at: https://aur.archlinux.org/packages/crumbs/

### macOS Homebrew Formula

On macOS you can install crumbs with [Homebrew](https://brew.sh) like this:

```shell
$ brew install mhubig/crumbs/crumbs
```

### Nix package

A package is available on the Nix package repository, for installing on Linux and macOS. It is currently being independently managed by [TheSola10](https://github.com/thesola10)

You can install crumbs like this:

'''shell
$ nix-env -iA nixpkgs.crumbs
'''

### Prerequisites

In order to compile and install crumbs on your local system you the following software must be available on the system:
1. [gcc](https://gcc.gnu.org/)
2. [make](https://www.gnu.org/software/make/)
3. [gzip](https://www.gnu.org/software/gzip/)
4. [git](https://git-scm.com/)

### Installation procedure

1. Checkout the sources from github.
```bash
git clone https://github.com/fasseg/crumbs.git
```

2. Run automake to create required files and the configure script. Optionally specify the installation path with `--prefix` and the path for the config file with `--sysconfdir`.
```bash
cd crumbs
automake --add-missing
./configure --prefix='/usr/local' --sysconfdir='/etc'
```

3. Compile the program.
```bash
make
```

4. Install the binaries and the man pages.
```bash
sudo make install
```

### Configuration file

The default configuration file is `/etc/crumbs.conf`. It contains the following settings:

`path`
>The path to use for storing data. If the path starts with a forward slash crumbs uses an absolute path to the configuration file. If the path is not starting with a forward slash the current user's home directory is prepended to the path.

A different configuration file can be used by invoking crumbs with the `--config` option
### Auto Completion

An auto completion file for the bash shell is included and installed in `/usr/local/share/crumbs/crumbs-completion.bash`. In order to enable the completion you can copy the file `crumbs-completion.bash` to e.g. `/usr/local/share/crumbs/` and source in your `.bashrc` file:
```bash
echo "source /usr/local/share/crumbs/crumbs-completion.bash" >> ~/.bashrc

```

### Usage

You can check the help dialog of the program or the man page for usage documentation and some examples:
```bash
crumbs --help 
man crumbs

```
