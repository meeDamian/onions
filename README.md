List of onionable stuff
=======================

This is a list of services integrateable easily with Tor.  Judge how well maintained it is by yourself.

It all assumes you have Tor installed, and running in background with mostly default configuration (Tor listens on `127.0.0.1:9050`).

* [Installation](#Install)
* [GnuGPG](#GnuGPG)


Install
-------
The easiest ways to install Tor I've found so far.

### MacOS

```bash
brew update
brew install tor
brew service start tor
tor --version
```

> **Note:** `torrc` is located in `/usr/local/etc/tor/torrc` by default.

### Debian/Ubuntu

That includes Raspbian on the more capable RBPs (not zero).

```bash
sudo apt update
sudo apt install tor
sudo service tor@default restart
```

> **Note:** `torrc` is located in `/etc/tor/torrc` by default.

GnuGPG
------
To use `hkps://keys.openpgp.org`, but through a hidden service:

https://keys.openpgp.org/about/usage 

To file `~/.gnupg/gpg.cong`, add (or replace `keyserver …`) line:

```
keyserver hkp://zkaan2xfbuxia2wpf7ofnkbz6r5zdbbvxbunvp5g2iebopbfc4iqmbad.onion
```

Should work on MacOS & Linux alike.
