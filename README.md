Sapwood CLI
==========

**WARNING! This is ready to be used, but it is built to work closely with
[Sapwood Developer](https://github.com/seancdavis/sapwood-developer), which is
not yet ready for use.**

Sapwood's command-line interface abstracts much of the maintenance of Sapwood
from your developers and designers, keeping them focused on developing and
designing.

This project is brand new, so there will exist some kinks to work out with
different environment setups.

Installation
----------

Sapwood CLI is packaged as a Ruby Gem, and it's best to install it globally on
your machine.

```text
$ gem install sapwood
```

Usage
----------

Sapwood CLI comes packaged with an executable (hence the *CLI*), as `sapwood`.
It will always take an *action* as its first argument, like this:

```text
$ sapwood [ACTION]
```

See below for details on the actions.

Actions
----------

### Install

Install will install the [Sapwood Developer
application](https://github.com/seancdavis/sapwood-developer) into
`~/.sapwood`. Therefore, *you only have to run this once*.

This will go through a series of questions to ensure it is installed properly.

> **WARNING! You must have a production Sapwood app and database running
> remotely before you can install Sapwood locally**.

```text
$ sapwood install
```

### Start

This starts the Sapwood (Rails) server as a daemon on your local machine.

> *Note: It can take several seconds to get started, considering your database
> is remote.*

```text
$ sapwood start
```

> Pay attention to the output. The output will tell you how to access the
> Sapwood Developer application.

### Stop

Stops the Sapwood (Rails) server (kills the daemon process).

```text
$ sapwood stop
```

### Restart

Stops and then starts the Sapwood (Rails) server.

```text
$ sapwood restart
```

### Update

Updates the Sapwood Developer application.

It's important that your developer application and the production application
are on the same major version (of which there is only one now). But it's also
good to stay updated so you get all the development features. This simply runs
a `git pull` on your Sapwood Developer repo.

```text
$ sapwood update
```

### Link

Links a project to the Sapwood Developer application.

If you're familiar with Sapwood, then you know it's (currently) all about the
symlinks from a project directory to the necessary location in the rails app.
Nothing changes here. We're going to first symlink your project (from anywhere
on your machine) to the `~/.sapwood/projects` directory, and then into the
rails app itself.

**WARNING! This command MUST be run from inside a project directory of a
project that exists within the Sapwood database.**

*Note: Your local repository directory name MUST be named after either the slug
or the primary domain for that project. Otherwise, it will fail.*

```text
$ cd /a/sapwood/project/directory
$ sapwood link
```

### Log

Tails the log for the Sapwood Developer application. It's like mimicking what
happens when you run the `rails server` command in the foreground.

You can quit this process with `Cmd`+`C`.

```text
$ sapwood log
```

Contributing
----------

You're welcome to fix any bugs or add any small features to interact with the
developer app. However, at this point, if you want to be involved, I need much
more help with the Developer and Builder apps themselves, versus the interface
for working with them.
