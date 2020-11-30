# First Threat (Functions Check)
Let's take some time to both validate functionality of all tooling, as well as demonstrate general usage of your new 
"mini-range".

1. From your terminal run $`vagrant ssh elastic` to remotely access the "elastic" logger / attacker box.

> Your prompt will update to the following `[vagrant@elastomic ~]$`.

1. Enter `pwsh` to drop into a Powershell prompt. Now it is time to choose what test or attack you would like to run against the remote Windows 10 box.

1. You can browse the available tests by referencing the [Atomic Redteam Docs](https://github.com/redcanaryco/atomic-red-team/blob/master/atomics/Indexes/Indexes-Markdown/windows-index.md).

1. For this demonstration we will conduct a Mimikatz test for technique "T1059.001 TestNumber 1". This will use Powershell to download Mimikatz and then dump credentials on the system.

1. Before we can run this test against the Windows 10 box we first need to setup a Powershell Session over SSH to the Windows 10 box

1. Run the following command:  

    `$sess = New-PSSession -Hostname 192.168.33.11 -Username vagrant`

    > Here we create a variable (`$sess`) and set it to our new session we just created using the Powershell cmdlet New-PSSession.

1. You will prompted to accept the host and enter the password (vagrant).

1. Now in order  The syntax to launch an attack against a remmote host is as follows:

```shell
Invoke-AtomicTest     # Run Atomic Test
T1059.001             # Technique ID 
-TestNumbers 1        # TestNumber 
-Session $sess        # use our Session variable
```

1. Run the following command to kick things off:

    `Invoke-AtomicTest T1059.001 -TestNumbers 1 -Session $sess`

1. Once complete now go back to your Discover tab in Kibana.

1. In the search bar type "`Mimikatz`" and hit Enter. You should see results filtered to show the events matching the Mimikatz attack you just executed.


## Cleanup


1. Now most if not all AtomicRedTeam tests come with a cleanup command to clean up your test system before executing another test.

1. In order to cleanup our Mimikatz test we can run the same command we used to execute it this time with a `-Cleanup` option at the end.

1. Run the following command to clean house: 

    `Invoke-AtomicTest T1059.001 -TestNumbers 1 -Session $sess -Cleanup`


## Taking Things Further

Now you can dig into all of the events and start building detections based off of what logs its behavior produces after which you could run the test again to verify your detection logic is sound.

1. You can do this by buidling your query using KQL or Lucene and then going to the "Detections" tab in Kibana and selecting "Manage Detection Rules".

Congratulaltions you have executed your first test and hopefully wrote meaningful behavior based detections in order to help detect that activity in the future.

## Shutdown 
> A.K.A "It's broken and I dont know what to fix"

Once you are done playing in your sandbox, you need to clean things up. If you are in the middle of something and want to continue later, invoke a `vagrant suspend`. Otherwise, if you are done for the day invoke a `vagrant halt`. 

Last but not least, if you have goofed up your install you can use `vagrant reload`.

`vagrant --help` is your friend.



