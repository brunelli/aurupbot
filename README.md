AUR Update Bot
==============

This script automatically updates packages that make use of the
[`pkgver()` function](https://wiki.archlinux.org/index.php/VCS_package_guidelines#The_pkgver.28.29_function)
on its PKGBUILD.

This is very usefull when maintaining [VCS-based packages](https://wiki.archlinux.org/index.php/VCS_package_guidelines)
that feature extremely frequent changes that typically don't require manual intervention.

## How to use

```
Usage: aurupbot [ OPTIONS ] [ PKGNAMES ]
 
Options:
  -d or --dir <path>    Save files in <path> instead of /tmp.
  --disable-push        Doesn't attempt to push the updated files to AUR. 
  --email <email>       Send reports to <email>.
  --ignore <pkg(s)>     Ignore <pkg>. Use commas to pass various pkg.
  --nocolor             Disable coloring.
  -n or --notify        Use libnotify to send desktop notifications. 
  --reuse-dirs 	        Don't overwrite existing directories.
  -u or --user <user>   Check updates for all packages maintained by <user>.
  --config <file>       Source <file> for configuration.
  -h or --help 	        Print this message.

Configuration:
  You can have an user specific configuration file in ~/.config/aurupbotrc.
  An example file can be found in /etc/aurupbotrc.
```

## How to install

Get the package `aurupbot` from AUR.

## How it works

1. Download/update the package repository (`git`)

2. Check for updates (`makepkg`)

3. Build new version (`makepkg`)

4. Check package for errors (`namcap`)

5. Build SRCINFO file (`mksrcinfo`)

6. Commit and push changes to AUR (`git`)
