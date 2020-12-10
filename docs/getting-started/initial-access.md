# Initial Access

Now it's time to really get into things.


## Getting Status

Now that we've deployed, let's make sure everything is up and running. So, fire `stationctl` back up and let's do that.

`sh stationctl`, select `2. Status`.

This will run through a check of the Vagrant boxes, VirtualBox machines, and the status of Elasticsearch and Kibana.

Of note, because Elasticsearch is only a single node installation, the status will always be Yellow. Everything is fine.

![](../images/ts-status.png)

## Interface Login

The environment is designed for users to interact with 2 primary interfaces:

1. **Atomic Redteam - Execute Threats**

This adversary emulation toolset is accessed by sshing into the "elastic" box and starting a powershell session.

- From the $(pwd)/vagrant directory, `ssh` to the elastic vbox:
    - $`vagrant ssh ts.elastomic`
- start a powershell session
    - $`pwsh`

View the [usage guide](../toolset/image.md) to learn more about executing Atomic Red Team.

1. **Kibana WebUI - Detect Threats**

    - To reach Kibana browse to `localhost:5601`

        Kibana Credentials
        user: `vagrant`
        pass: `vagrant`

    - Once in Kibana click the 3 hash dropdown menu in the upper left corner of the UI and select the "Discover" tab.

    > Ensure that the timepicker is set to the most recent timeframe, example "Last 24 hours".
