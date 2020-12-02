# Deployment

Once you have all the requirements installed, it's time to deploy the mini-range.


## Build the Range

Once all the tools have been install, it's time to deploy the local range.

TODO: update below block to reference `stationctl` cli when complete.

1. Move into this repo's vagrant directory. Example: `cd thremulation-station/vagrant`
1. Kick of the import / build / provisioning of all machines: `vagrant up`
1. Get yourself some :coffee: , this will take 10-20 min depending on your connection

> **Note:** This is a bandwidth-intensive task that will download all the boxes that you selected. These downloads will only happen the first time you deploy. Drink you cup very very slowly?


## Initial Access

This lab environment is designed for users to interact with 2 primary interfaces:

1. **Atomic Redteam - Execute Threats**

This adversary emulation toolset is accessed by sshing into the "elastic" box and starting a powershell session.

- ssh to the elastic vbox:
    - $`vagrant ssh elastic`
- start a powershell session
    - $`pwsh`

1. **Kibana WebUI - Detect Threats** 

    - to reach Kibana browse to `localhost:5601`

        Kibana Credentials
        user: vagrant
        pass: vagrant

    - once in Kibana click the 3 hash dropdown menu in the upper left corner of the UI and select the "Discover" tab.
    
    <br>

    > Ensure that the timepicker is set to the most recent timeframe, example "Last 24 hours".