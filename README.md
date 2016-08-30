## dotfiles

A collection of miscellaneous .files (and some regular files). Files can be saved anywhere in the repository, and symlinked to the actual files in their correct different locations on the system.

Important files:

* `links` – The list of files to manage
* `symlinks.sh` – Setup symlinks
* `copy.sh` – Destroy symlinks by copying .files over them
* `osx.sh` – Some OS X configuration

## Setup

#### Clone

Clone to a local directory, like `~/.dotfiles`, and set scripts as executable:

```bash
$ cd ~
$ git clone https://github.com/maximn/dotfiles.git
$ mv dotfiles .dotfiles
$ cd .dotfiles/
```

#### Setup symlinks

This will *override* all existing files with a symlink to the new repository, losing anything you have in current files. If you have any important configuration in current .files, make sure to *first* save it to the cloned repo, and only then run the script:

```bash
$ ./symlink.sh
```

### OS X

Run `./osx.sh` for some sane OS X config settings and other custom setup (like adding the `subl` command for ST).

## Remove

If you decide you don't want the symlinks anymore, and want the full files in the right locations, run:

```bash
$ ./copy.sh
```

This will copy every file from `~/.dotfiles` to it's respective place, overriding the symlinks.

## Add New File

You can add a new .file (or any other config file for that matter) pretty easily:

1. Copy the existing file to anywhere in the repo, chose the most logical path (the place you save the file in the repo doesn't have to correspond to the actual real path on the system where the original file is – chose whatever's most convenient for you). It makes sense to group multiple related files into appropriately named folders. File names must be identical to the actual ones on the system.

2. Add the new file to the `links` file. The format is:

```
/path/on/system/.my-file1, /path/in/repo/.my-file1
/path/on/system/with\ space/.my-file2 /path/in/repo/.my-file2
```

See `links` for more details and examples.

## Homebrew

The `.brew` file maintains a list of all installed homebrew formulae. To update it:

```bash
$ brew leaves > .brew
```
