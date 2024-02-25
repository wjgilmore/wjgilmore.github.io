---
layout: post
title: "Configuring Hack The Box on MacOS"
published: false
---

I'm running an M1 (Apple Silicon) and so had to prefix the brew commands with `arch -arm64`:

```
$ arch -arm64 brew update
$ arch -arm64 brew install openvpn
```

Then to run the VPN:

```
$ sudo openvpn ~/Downloads/lab_wjgilmore.ovpn
...
2023-12-30 16:57:37 Timers: ping 10, ping-restart 120
2023-12-30 16:57:37 Protocol options: explicit-exit-notify 1
```

Later you'll need to use `telnet`, so might as well do so now:

```
$ arch -arm64 brew install telnet
```
