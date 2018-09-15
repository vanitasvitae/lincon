# Lincon - Link config files into a repository

Lincon is a script that helps you to manage configuration files of linux machines using a versioning system (like git).

Its two main functions are adding existing config files to your repository structure and deploying files from your repository to the system.

Lincon does NOT handle versioning for you. You could use git for example.

## Usage

To get started, create your config repository and copy the lincon script into it. In the following examples we assume that your repo is located in `/home/user/configs`.

Whenever you want to execute an operation with lincon, make sure that you are in your repositories root.

In order to add an existing config file to your repo, just call

```bash
$ ./lincon add /etc/someprogram/whatever.conf
```

Note that you always have to pass the absolute path to the script.

lincon now moves the config file to `/home/user/configs/etc/someprogram/whatever.conf` and creates a hardlink at `/etc/someprogram/whatever.conf`.

If you want to deploy a config file from your repo to the system, just call 

```bash
$ ./lincon deploy /etc/otherprogram/settings.conf
```

The command will create a hardlink at `/etc/otherprogram/settings.conf`, which points to the file in your repository (in this case `/home/user/configs/etc/otherprogram/settings.conf`.

In case there is already a config file with the same name, the file will get backed up to `/etc/otherprogram/settings.conf.bak`.
