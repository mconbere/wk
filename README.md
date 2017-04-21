# wk

**wk** is a simple commandline tool to automatically set up a workspace. Instead of maintaining global environment variables in a complex `.bashrc`, **wk** allows you to create a `.wk` script in a directory and just the environment variables from the directory you are in will be set.

## Install

To install **wk** copy the script to any directory in your PATH.

## Setup

For any workspace that needs workspace specific scripts run, create a an executable script named `.wk` in the root directory of the workspace. For instance, to set your GOPATH you would add the following `.wk` file in the root directory of a Go workspace:

```
#!/bin/bash

export GOPATH=$PWD
```

## Usage

To use **wk**, simply prepend any command you normally run with `wk`. It will execute the remaining command line arguments after it runs the setup scripts.

```
$ wk go build .
```

## Advanced Usage

### Nested workspaces

**wk** allows nested workspaces. All directories from root to your current working directory are inspected for `.wk` files, and they are executed in order.

### WKDIR

**wk** sets a special environment variable for `.wk` scripts called `WKDIR`. This variable provides a unique directory inside of the user's home directory to store workspace specific files.

## Future Work

- Set up a shell to automatically run `wk` by default.
- Allow post-command cleanup actions in .wk scripts.
- World domination.
