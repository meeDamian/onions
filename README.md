List of onionable stuff
=======================

This is a list of services integrateable easily with Tor.  Judge how well maintained it is by yourself.

It all assumes you have [Tor installed](#Install-Tor), running in background, and listening on `127.0.0.1:9050`.

### Index

* [Bitcoin Git Repos](#Bitcoin-Git-Repos)
* [GnuGPG](#GnuGPG)
* [Keybase](#Keybase)
* [Honorable Mentions](#Honorable-Mentions)
* [LNCM](#LNCM)


Bitcoin Git Repos
-----------------

Thanks to [@laanwj], Bitcoin and some orbiting repos (`lnd`, `c-lightning`, `eclair`, Bitcoin meta stuff) are mirrored as a Tor hidden service at:

[@laanwj]: https://github.com/laanwj

```
nxshomzlgqmwfwhcnyvbznyrybh3gotlfgis7wkv7iur2yj2rarlhiad.onion
```

While all necessary instructions are on [the website above], here's the **tl;dr:**

[the website above]: http://nxshomzlgqmwfwhcnyvbznyrybh3gotlfgis7wkv7iur2yj2rarlhiad.onion

#### Fresh clone of Bitcoin

```bash
git -c http.proxy=socks5h://127.0.0.1:9050 clone http://nxshomzlgqmwfwhcnyvbznyrybh3gotlfgis7wkv7iur2yj2rarlhiad.onion/git/bitcoin.git
cd bitcoin
git config --add remote.origin.proxy "socks5h://127.0.0.1:9050"
```

#### Change `origin` of lnd to Tor

```bash
cd lnd
git remote set-url master http://nxshomzlgqmwfwhcnyvbznyrybh3gotlfgis7wkv7iur2yj2rarlhiad.onion/git/lnd.git
git config --add remote.master.proxy "socks5h://127.0.0.1:9050"
git remote add github git@github.com:lightningnetwork/lnd.git
```

GnuGPG
------

To use `hkps://keys.openpgp.org` through a hidden service, to `~/.gnupg/gpg.cong` file add the following line:

```
keyserver hkp://zkaan2xfbuxia2wpf7ofnkbz6r5zdbbvxbunvp5g2iebopbfc4iqmbad.onion
```

If you already have a `keyserver …` line there, replace it.

[Onion source](https://keys.openpgp.org/about/usage). Should work on MacOS & Linux alike.

Keybase
-------

Keybase talks about their usage of Tor in more detail on [this page] [(clearnet)], but here's a **tl;dr:**

[this page]: http://keybase5wmilwokqirssclfnsqrjdsi7jdir5wy7y7iu3tanwmtp6oid.onion/docs/command_line/tor
[(clearnet)]: https://keybase.io/docs/command_line/tor

#### CLI

Tor hidden address is used by the CLI internally by default.

Enabling CLI's communication with **non-keybase** services via Tor can be done with either:

```bash
keybase config set tor.mode leaky
keybase config set tor.mode strict
```

> **Note:** both modes are fairly broken as of 2019-08-23 & `v4.3.2`

#### Web

You can visit Keybase through their hidden service at:

```
keybase5wmilwokqirssclfnsqrjdsi7jdir5wy7y7iu3tanwmtp6oid.onion
```

#### Desktop

You can proxy all desktop client traffic through Tor by setting PROXY to `SOCKS5`,
`127.0.0.1`, and `9050` in `Keybase -> Settings -> Advanced`.


Honorable Mentions
------------------

These services are known for using Tor either extensively, or exclusively:

<!-- TODO: add links -->
* Samourai Wallet
* Wasabi Wallet

LNCM
----
A Chiang Mai-based Lightning Network oriented developer community.  Here's some of our onions:

#### ⛓ Bitcoin nodes

| type    | addresses     |
|---------|:--------------|
| mainnet | `lncmdma3namzrbnx.onion:8333` <br> `lncmdmx7ezlplcck.onion:8333` <br> `lncmdmgoddecttey.onion:8444`   |
| testnet | `lncmdmfl674xg3oa.onion:18333`<br> `lncmdmrpdhoeraa5.onion:18333`  |
| regtest | N/A at the moment |

#### ⚡️ Lightning nodes

| type    | connection string |
|---------|:------------------|
| mainnet | `032260c3b64b471b7eb0630b4af5d07ca94ff4e759573cbbe1bfb25845c375ed6e@o3s5j4j37nbyzgvbngn3ahpmttvviyensw34klhqzw7in7vfzz646lqd.onion:9735` |
| testnet | `02e888295220a5254a5f0486538dc77c0357ee9727db2e9173e6a76646d4aa332e@hxz6xeqvmi5s6rbqqtgu4qkihgdkwbnc7h2vnsn3qkahhffau6afbsyd.onion:9733` |
| regtest | N/A at the moment |

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
