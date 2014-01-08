# dvm

An on demand [Docker][docker] virtual machine, thanks to [Vagrant][vagrant] and [boot2docker][boot2docker]. Works great on Macs and other platforms that don't natively support the Docker daemon. Under the covers this is downloading and booting Mitchell Hashimoto's [boot2docker Vagrant Box][boot2docker_vagrant_box] image.

## <a name="mac-tl-dr"></a> tl;dr for Mac Users

Are you already a Vagrant user using Virtualbox? Use Homebrew? Great!


```sh
# Install Docker Mac binary
brew install docker

# Install dvm
brew install https://raw.github.com/fnichol/dvm/master/homebrew/dvm.rb

# Bring up your Vagrant/Docker VM
dvm up

# Set a DOCKER_HOST environment variable that points to your VM
eval $(dvm env)

# Run plain 'ol Docker commands right from your Mac
docker run ubuntu cat /etc/lsb-release
```

p.s. No Vagrant or VirtualBox installed? Check out the [Requirements](#requirements) section below.

## <a name="requirements"></a> Requirements

* [VirtualBox][virtualbox_dl], version 4.3.4+
* [Vagrant][vagrant_dl], version 1.4.0+
* (*Optional*) [Docker][docker_dl], version 0.7.3+ or use the [Docker Remote API][docker_api]

## <a name="install"></a> Install

Installation is supported for any Unixlike platform that Vagrant and VirtualBox support.

```sh
wget -O dvm-0.2.1.tar.gz https://github.com/fnichol/dvm/archive/v0.2.1.tar.gz
tar -xzvf dvm-0.2.1.tar.gz
cd dvm-0.2.1/
sudo make install
```

### <a name="intsall-homebrew"></a> Homebrew (Mac)

There is a vendored Homebrew formula which can be installed with:

```sh
brew install https://raw.github.com/fnichol/dvm/master/homebrew/dvm.rb
```

## <a name="usage"></a> Usage

Bring up help with:

```
$ dvm --help

Usage: dvm [-v|-h] command [<args>]

Options

  --version, -v - Print the version and exit
  --help, -h    - Display CLI help (this output)

Commands

  check           Ensure that required software is installed and present
  destroy         Stops and deletes all traces of the vagrant machine
  env             Outputs environment variables for Docker to connect remotely
  halt, stop      Stops the vagrant machine
  reload          Restarts vagrant machine, loads new configuration
  resume          Resume the suspended vagrant machine
  ssh             Connects to the machine via SSH
  status          Outputs status of the vagrant machine
  suspend, pause  Suspends the machine
  up, start       Starts and provisions the vagrant environment
  vagrant         Issue subcommands directly to the vagrant CLI
```

Keep in mind that dvm thiny wraps Vagrant so don't hesitate to use raw Vagrant commands in your `$HOME/.dvm` directory. Or use the `dvm vagrant` subcommand from anywhere:

```
$ dvm vagrant --version
Vagrant 1.4.2
```

Bring up your VM with `dvm up`:

```
$ dvm up
Bringing machine 
