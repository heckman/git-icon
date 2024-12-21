# git-icon

A command-line utility for MacOS that applies
a git icon to folders that look like git repositories.

It can also revert the icons back to the system default.

## Usage

```
git-icon set [dir...]
git-icon reset [dir...]
```

Recursively set or unset the folder-icon of specified directories, and their
descendents, that look like git repositories. If no directories are specified,
the current working directory and its descencents are searched.

Directories "look like git repositories" if they contain a .git subdirectory.

## Requirements

This script requires `fd` and `fileicon`. Both are available via homebrew.

The `fd` requirement can be circumvented by modifying the source to use `find`,
but in my experience `fd` works in half the time that `find` does;
your milage may vary.

## Installation

This script can be run from anywhere.

You'll need to modify the source to specify the path to the icon.
It should be a relative path.
I've included a suitable icon in the `lib` directory of this repo.

Icon requirements are as they are for the `fileicon` command:

- The Icon can be of any system-supported image format.
- Images will be downscaled to 512px x 512px.
- Non-square images will be distorted.

## Icon\$'\r' files

MacOS will create these files to hold the custom icon information.

If you want to prevent them from littering your repositories
you should modify your global git ignore settings.
It turns out this is not trivial, as the syntax for `.gitignore` files
makes no accommodation for the representation of non-printable characters.

After referencing
[this answer](https://stackoverflow.com/questions/17556250/how-to-ignore-icon-in-git/65429032#65429032)
(not the accepted one answer)
on Stack Overflow
my global git ignore includes this chunk:

```gitignore
# To catch the Icon$'\r' files created by MacOS for custom folder icons:
Icon?
# where ? matches any character, and un-ignore legit Icon* files:
![iI]con[][ !"#$%&'()*+,-./0-9:;<=>?@A-Z\^_`a-z{|}~]
# that should be all the printable 7-bit ASCII
# it won't catch tabs, newlines, etc, but I'm OK with that.
# UTF-8 seem to be fine, perhaps because it's more than one byte.
```

If this isn't working for you, [make sure git knows where to find your global git ignore file](https://stackoverflow.com/questions/7335420/global-git-ignore/7335487#7335487).

(I also have `.DS_Store` in a `~/.gitignore_global` file.)

## Licensing

Everything except the Git logo is licensed under the MIT License.

The Git logo, by [Jason Long](https://jasonlong.me/), is licensed under the [Creative Commons Attribution 3.0 Unported License](https://creativecommons.org/licenses/by/3.0/).

I've altered the Git logo's _svg_ code to place the original 92-point image on a 120-pt transparent background. This keeps it from appearing too large in the Finder.
