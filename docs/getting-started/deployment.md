# Deployment


## Build the Range

Once all the tools have been install, it's time to deploy the local range.

TODO: add deploy script here

1. Move into this repo's vagrant directory: `cd ThreatEmulation-DetectionLab/vagrant`

1. Kick of the import / build / provisioning of all machines: `vagrant up`

1. Get yourself some :coffee: , this will take a sec

> By a "sec", @seven62 means like 15-20 min. Drink you cup very very slowly.


## Initial Access

This lab environment is designed for users to execute and detect threats by interacting with 2 primary interfaces:

1. **Kibana WebUI**

- to reach Kibana browse to `localhost:5601`

        Kibana Credentials
        user: vagrant
        pass: vagrant

- once in Kibana click the 3 hash dropdown menu in the upper left corner of the UI and select the "Discover" tab.

> Ensure that the timepicker is set to the most recent timeframe, example "Last 24 hours".

1. **Atomic Redteam**

This adversary emulation toolset is accessed by sshing into the "elastic" box and starting a powershell session.

- ssh to the elastic vbox:
    - $`vagrant ssh elastic`
- start a powershell session
    - $`pwsh`