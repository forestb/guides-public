# wsl-debian9-to-debian11<!-- omit in toc -->

When setting up Debian in WSL, the default version available is Debian 9 (code name: "Stretch"), released June 17th, 2017.  The latest version is Debian 11 (code name: "Bullseye"), released August 14th, 2021.

Since needing to repeat these steps was likely to be frequent, I created this guide.

- [Upgrade](#upgrade)
- [Verify](#verify)
- [Credit](#credit)

# Upgrade

Ensure your system is up to date:
```bash
sudo apt update
sudo apt full-upgrade
```

Remove unused dependencies:
```bash
sudo apt autoremove
```

Make sure you're at the home directory:
```bash
cd $HOME
```

Update `/etc/apt/sources.list` to look something like this:
```bash
deb http://deb.debian.org/debian/ bullseye main
deb-src http://deb.debian.org/debian/ bullseye main

deb https://security.debian.org/debian-security bullseye-security main
deb-src http://security.debian.org/debian-security bullseye-security main

deb http://deb.debian.org/debian/ bullseye-updates main
deb-src http://deb.debian.org/debian/ bullseye-updates main
```

Tip for editing the protected file:
```bash
sudo nano /etc/apt/sources.list
```

Save file in nano: `ctrl+x`.

Verify the file is updated:
```bash
cat /etc/apt/sources.list
```

Start the upgrade:
```bash
sudo apt update
sudo apt upgrade
```

![](./assets/2022-04-26_22-09-30.png)

Once the partial upgrade completes, do the full upgrade:
```bash
sudo apt full-upgrade
```

# Verify

Check to see what version of Linux you're running
```bash
cat /etc/os-release
```


# Credit
* https://linuxnightly.com/how-to-upgrade-debian/