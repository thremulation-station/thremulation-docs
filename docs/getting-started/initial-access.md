# Initial Access

Now it's time to really get into things. 


## Getting Status

stationctl status
TODO


## Interface Login

The environment is designed for users to interact with 2 primary interfaces:

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