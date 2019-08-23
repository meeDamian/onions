List of onionable stuff
=======================

This is a list of services integrateable easily with Tor.  Judge how well maintained it is by yourself.

It all assumes you have [Tor installed](#Install-Tor), and running in background with mostly default configuration (Tor listens on `127.0.0.1:9050`).

### Index

* [GnuGPG](#GnuGPG)


GnuGPG
------
To use `hkps://keys.openpgp.org` through a hidden service, to `~/.gnupg/gpg.cong` file add the following line:

```
keyserver hkp://zkaan2xfbuxia2wpf7ofnkbz6r5zdbbvxbunvp5g2iebopbfc4iqmbad.onion
```

If you already have a `keyserver …` line there, replace it.

[Onion source](https://keys.openpgp.org/about/usage). Should work on MacOS & Linux alike.


Install Tor
-----------
The easiest ways to install Tor I've found so far.

### MacOS

```bash
brew update && brew install tor && brew service start tor && tor --version
```

> **Note:** `torrc` is located in `/usr/local/etc/tor/torrc` by default.

### Debian/Ubuntu

That includes Raspbian on the more capable RBPs (not zero).

```bash
sudo apt update && sudo apt install tor && sudo service tor@default restart && tor --version
```

> **Note:** `torrc` is located in `/etc/tor/torrc` by default.
