# Welcome

<!-- Thanks for visting the techincal documentation for the Thremulation Station projec -->

<br>
<p align="center">
<img src="images/ts-logo-temp.png" width="50%" alt="">
</p>
<br>


Thremulation Station is an approachable and small-scale threat emulation and detection range. It's a collection of open source tools that when working together, enable a _reasonably_ spec'd machine serve as a cyber threat detection and emulation range. Bottom line: ***a cyber threat lab for your laptop***.

!!! info "TL;DR"
    If you're ready to skip the reading and jump into things, head to the [getting started / installation](../getting-started/installation.md).

There are a lot of tools and moving pieces, but the main building blocks are:

- Virtualbox
- Vagrant
- Elasticsearch
- Kibana
- Elastic Endpoint Agent
- Atomic Red Team
- Caldera


## Project Goals

Our goal from the very beginning has been to provide the following:

1. lightweight range that can operate on a laptop with a _minimum_ of 4 threads and 8G of RAM
1. support the big 3 host operating systems (initial linux path is RHEL-based)
1. present users a smooth path to execute threats and observe them with Elastic 
1. provide a singular TUI (Station Control) that can be used to manage all aspects

!!! note "Note"
    You'll be introduced to `./stationctl` early in the [Getting Started](/getting-started/deployment/#introduction-to-station-control) section and use it to deploy boxes, get status, manage and clear data, and much more. A full reference guide is located at [support / stationctl](/support/stationctl.md).



## Getting Help

There are several ways to connect with the project community whether that's for support, contributing content, or just learning from other infosec nerds. The primary method should be [Discord](https://discord.gg/mtNXN4QjHh)!

!!! info "Info"
    Discord server invite URL [https://discord.gg/mtNXN4QjHh](https://discord.gg/mtNXN4QjHh)

- issues: [github.com/thremulation-station/issues](https://github.com/thremulation-station/thremulation-station/issues)
- twitter: [@thremulation](https://twitter.com/@thremulation)
- email: `contact [at] thremulation [dot] io`



## Contribution

How can I help, you ask? We welcome contributions, so check out the project repo [contribution page](https://github.com/thremulation-station/thremulation-station/blob/devel/CONTRIBUTING.md) on Github.
