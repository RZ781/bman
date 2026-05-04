# bman
`bman` is a package manager that pulls software from upstream sources and builds
it locally. Packages do not come from a repository, so you can simply create any
packages you need by giving the URL of a repo and any other information needed,
such as a build command.

For example, to install the Linux kernel:
```
bman install linux \
    'https://git.kernel.org/pub/scm/linux/kernel/git/stable/linux.git' \
    --build "make defconfig -j$(nproc) && make -j$(nproc)" \
    --branch linux-rolling-stable
```
This will clone the linux-rolling-stable branch of the Linux repository, then
generate the default config and build it. After running `bman update`, the
repository will be pulled from and the commands run again if there are updates.
You can also use an existing config file:
`bman install-config linux linux.json`

bman is free software, distributed under the terms of the GNU General Public
License as published by the Free Software Foundation, either version 3 of the
License or (at your option) any later version. See the file COPYING for more
information. License copyright years may be listed using range notation, e.g.,
1996-2015, indicating that every year in the range, inclusive, is a
copyrightable year that would otherwise be listed individually.
