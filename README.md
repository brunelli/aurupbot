AUR Update Bot
==============

This script automatically updates packages that make use of the
[`pkgver()` function](https://wiki.archlinux.org/index.php/VCS_package_guidelines#The_pkgver.28.29_function)
on its PKGBUILD.

This is very usefull when maintaining [VCS-based packages](https://wiki.archlinux.org/index.php/VCS_package_guidelines)
that feature extremely frequent changes that typically don't require manual intervention.

Requires [AUR 4](https://wiki.archlinux.org/index.php/Arch_User_Repository#AUR_4).

## How to use

```
Usage: aur-updatebot PKGNAME [ PKGNAME... ] [ OPTIONS ]
 
Options:
  -d or --dir <path>    Save files in <path> instead of /tmp.
  --disable-push        Doesn't attempt to push the updated files to AUR. 
  -n or --notify        Use libnotify to send desktop notifications. 
  -u or --user <user>   Check updates for all packages maintained by <user>.
  -h or --help 	        Print this message.
```

## How it works

1. Download the package repository (git)

2. Check for updates (makepkg)

3. Build new version (makepkg)

4. Check package for errors (namcap)

5. Build SRCINFO file (mksrcinfo)

6. Commit and push changes to AUR (git)
