---
title: NTP Server
feed: show
date: 2021-11-01
---

Port: 123 UDP

The Network Time Protocol (NTP) is a protocol designed for accurately synchronizing local time clocks with networked time servers. The NTP network of time servers is set up as a hierarchical manner, such that any user can enter the system as a server at some level (see the Wikipedia page for more details).

The NTP hierarchy is separated into different levels, called clock strata. The most accurate level, Stratum 0, is reserved for atomic clocks, etc. The next level, Stratum 1, is generally used by networked machines locally connected to the Stratum 0 clocks. Stratum 2...15 are NTP machines that are connected, in turn, to lower level clocks and each other.

# Install Server
To install a server, simply use chrony:

```bash
apt update 
apt install chrony
```

If you want to serve the network times, you will need to add the following line to `\etc\chrony\chrony.conf`

```\etc\chrony\chrony.conf
allow {CIDR}
```

## Run chrony in an container
Chrony tries to update the system clock, which - in a container - is managed by the host system. So chrony will fail to start. To run chrony in a container, the -x option has to be set.

# Test NTP Server
To test a NTP server, install `ntpdate`

```bash
apt update
apt install ntpdate
```

then simply run:

```bash
ntpdate -q {server address}
```