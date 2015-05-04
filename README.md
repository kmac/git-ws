git-ws
======

`git-ws` is a shell script which performs operations on a related set of git-controlled directories contained within a common subdirectory 'workspace'.

It allows git commands to be applied across a set of workspace directories. A common example is to query the status of all the git repositories in your workspace:

    git ws status


Will run `git status` across all of the git directories in the workspace defined by `$GIT_WORKSPACE`.


#### GIT_WORKSPACE

GIT_WORKSPACE is an environment variable specifying the workspace directory. It can be overridden usind the `-d <dir>` argument.


#### Usage

From the help:

    Usage: git-ws [-d <dir>] [-f] [-i] <cmd>
           git-ws -l
    Runs given git command on all git directories in $GIT_WORKSPACE
    
    Arguments:
    
      [-d <dir>] [-f] [-i] <cmd>:
          -d <dir>: use given directory instead of $GIT_WORKSPACE
          -f: force - ignore errors if they occur on individual directories
          -i: interactive - ask before running command on each directory
    
        <cmd>: The git command to execute.
               The 'git' part of the command is optional (assumed) and can be left out.
    
      -l: list - list the git directories in workspace
    
    Using a .gitwsinclude file
    The file ${GIT_WORKSPACE}/.gitwsinclude, if present, specifies a list of directories to include.
    If this file is given then only the files listed are included.
    Use one directory name per line in file, directory name only.
    
    Using a .gitwsignore file
    The file ${GIT_WORKSPACE}/.gitwsignore, if present, specifies a list of directories to ignore.
    Use one directory name per line in file, directory name only.
    
    Examples:
    git-ws git status     | short form: git-ws status
    git-ws git pull --rebase | short form: git-ws pull --rebase
    git-ws -i commit -am "WIP: commit checkpoint"
    git-ws -d /path/to/other/workspace status
    git-ws -l



