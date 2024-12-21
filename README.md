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

## Licensing

Everything except the Git logo is licensed under the MIT License.

The Git logo, by [Jason Long](https://jasonlong.me/), is licensed under the [Creative Commons Attribution 3.0 Unported License](https://creativecommons.org/licenses/by/3.0/).

I've altered the Git logo's _svg_ code to place the original 92-point image on a 120-pt transparent background. This keeps it from appearing too large in the Finder.
