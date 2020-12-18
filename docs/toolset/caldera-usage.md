# Caldera Basic Usage Lab



### Goals
At the end of this lab you will be able to:

1. Startup the Caldera server
2. Understand and use the Caldera interface
3. Configure and deploy a Caldera agent to a “victim” host 4. View and create adversary profiles
5. Create and run an operation
6. Hunt for operation activity in Kibana

### Pre-Req Setup for this Lab

Vagrant up the elastomic and windows10 box:

vagrant up ts.elastomic ts.windows10

Establish an RDP session with the windows10 box with the RDPclient of your choice, with the following data:

Host:192.168.33.11
User:vagrant
Password:vagrant

---

## Startup

Caldera comes pre-installed on the elastomic host, and is located in the /home/vagrant directory. In order to utilize it you only need to start up the Caldera server, so let’s do that.

1. Firstsshintotheelastomicboxwiththefollowingcommand:vagrantssh ts.elastomic

1. Onceyouaressh’dintoelastomicmoveintotheCalderadirectorywith the following command : cd caldera

1. NowtostartupourCalderaserverrunthefollowingcommandwhichwill startup the server and host it at localhost:8888 : python3 server.py — insecure

1. The server startup will take at most 30 seconds to initiate, after which we can validate by going to your local browser and browsing to http://localhost:8888. You should see the following:

<IMG>

## Interface

– Nowthatwehaveourserverrunninghostedlocallyonport8888wecan login and take a look around
– DefaultcredentialsforyourCalderaserverare(admin:admin)
– AftersuccessfullylogginginyoushouldseetheCalderawelcomepage

<IMG>

– Clickonthehamburgermenunexttonavigateinthetopleftcornerto display the different options Caldera provides

<IMG>

– Theprimarymenuoptionsyouwillbeconcernedwithforusagearethe agents, adversaries and operations selections

## Agents

– Wewillstartwiththeagentstabsogoaheadandclickitafterwhichyou will see the following screen

<IMG>

– Thistaballowsustoconfigure,createanddeployanagentononeofour “victim” boxes that will communicate back to our Caldera server where we can run our operations from
– Beforewecreateouragentletsexploresomeoftheupfront configuration options we have available
– Thefirstoptionisthebeacontimer
– Beacontimerallowyouspecifyhowlongyouragentwillwaittocheckin and send back data. By default these values, as you will see, are set to 30 and 60 which is fine. You may want to change these values if you are emulating a specific adversary or just trying to remain undetected from any network hunting the defender would be doing.

<IMG>

– Thesecondoptionisthewatchdogtimer
– Watchdogtimerletsyousetthenumberofsecondstowait,oncethe server is unreachable, before killing an agent.

<IMG>

– Thethirdoptionistheuntrustedtimer
– Untrustedtimersetsthenumberofsecondstowaitbeforemarkinga missing agent as untrusted.

<IMG>

– Thefourthoptionistheimplantname
– Thebasenameofnewly-spawnedagents.Ifnecessary,anextensionwill be added when an agent is created (ex: splunkd will
become splunkd.exe when spawning an agent on a Windows machine).

<IMG>

– Thefinaloptionavailabletousisthebootstrapability
– Bootstrapabilityisacomma-separatedlistofabilityIDstoberunona new agent beacon. By default, this is set to run a command which clears command history.

<IMG>

– Alrightnowthatweunderstandtheavailableconfigurationoptionslets go ahead and generate a new agent for us to deploy to our windows10 box
– Wearegoingtousethedefaultvaluesforthistestsogoaheadand choose “click here to deploy an agent” button and you will see the following option

<IMG>

– Ifyouclickthedropdownfor“Chooseanagent”youwillseeanumberof options

<IMG>

– Asyoucanseeeachoftheseagentsprovidesabriefdescription
– TheonlytwoIhaveutilizedandtestedarethe54ndc47andManxagents
– Forgeneralpurposesandeverydayuseyouwillusethe54ndc47agent as it was developed directly for use with Caldera
– Choosethe54ndc47agentandselectthe“Allplatforms”dropdownto choose your OS
– Forthislabwewillchoosewindowsforourwindows10host
– Fortheapp.contact.httpfieldyouwillsupplytheiporurlofyourCaldera server which in our case is 192.168.33.10:8888
– YouanseeCalderageneratesaPowershellcommandtodownloadand execute the Caldera GoLang agent on your windows10 host

<IMG>

– Nowcopythatcommandinfullandletsgoovertoourwindows10RDP session
– OpenaPowershellpromptasadministrator

<IMG> powershell   

– NowpasteyourCalderaagentPowershellone-linerandhitenterto download and execute the agent
– OncethisisdonewecangobacktoourCalderaserverGUI
– Clickthexinthetoprightcorneroftheagentselectionboxyouwerein and you should now see an agent has checked into the Caldera server

<IMG>

– Beforewemoveontoemulatingadversaryactivityletsexploresomeof the information the agent provides us
– Asyoucanseeifgivesauniqueagentid,thehost,protocol,agent
 
–
process id and if the agent is running in a privileged context or not
– Butifweclickonthegreenprocessidwecanseealotmoredetailtous

<IMG>

– Asyoucannowseewehaveamuchmoredetailedviewofouragentto include parent process id, location of our executable and the user we are running as
– Wealsoaregiventheabilitytoeditcertainfieldsdenotedby*andkill our agent
– Nowclickthexinthetoprighttoleavethisview


## Adversaries

– Selectthehamburgermenuinthetopleftofyourscreenandselectthe adversaries tab which will open and drop you down to the following screen

<IMG>

– Asyoucanseetheadversariestaballowsustocreateourowncustom profile (adversary) or view the profiles already created within Caldera
– Letstakealookatapre-madeadversaryprofilesowecanexplorewhat makes up a profile
– Clickthe“Selectanexistingprofile”dropdownandselecttheEnumerator profile

<IMG>

– Enumeratoristhenameoftheprofile
– EnumerateProcessesinallthewaysisadescriptionoftheprofile
– BeneathorderingyoucanseethechooseTTPsandinwhatorderthey are to be executed
– Thesearethebasicbuildingblocksofanadversary
– LetlookatwhatoneoftheseTTPslooklikeupclose
– ClickontheWMICProcessEnumerationblockandyoushouldseethe following screen

<IMG>

– HerewecanseeeverythingaboutthisspecificTTP.Youseeitsuniqueid, name, description, tactic, technique id and technique name.
– Belowthegenericinformationyoucanseewhatplatformitiscompatible with and what is being utilized to execute this technique
– Scrolldownfurtherandyouwillseethecommandthatisbeingexecuted along with a cleanup command if one exists and the timeout value for the command
– Nowclickthexinthetoprightcornerofthescreenandwewillcreate our own profile we will execute on our “victim”
– Underprofileschangethesliderfromviewtoadd

<IMG>

– I’mgoingtousetheprofilenameofTestbutyoucanusewhatevername you please
– NextIwillfilloutagooddescriptionformyprofilewhichforthiswillbe“A set of TTPs for displaying Caldera’s functionality”

<IMG>

– Nowletsaddsomeabilitiestoourprofile
– Clickthe+addabilityselectorontherightsideofyourscreenwhichwill pop up a familiar menu
– LetsselectaTTP
– Iwillselectthediscoverytactic,T1007SystemServiceDiscoveryand Discover System Services ability

<IMG>

– IfyouscrolldownyouwillseethecommandbeingrunisthePowershell cmdlet Get-Service executed by Powershell as evidenced by the psh executor
– Nowletsclickthegreenaddtoadversarybuttoninthebottomleftofthe screen to add this TTP to our profile
– AsyouseewenowhaveaddedthisTTPasthefirststepinourattack

<IMG>

– I’veaddedasecondattackabilityandyoucanaddasmanyasyouwish but for my purposes here this will be fine
– Letssavethisprofileandmoveontoexecutingitwithouragentonthe windows10 box
– OncesavedyouwillseeAdversarySaved!atthebottomofyourscreen

<IMG> adversary saved!



## Operations

– ScrollupandclickthehamburgermenuinthetopleftoftheCaldera interface and select the Operations tab to display the following screen

IMG

– Therearecurrentlynooperationscreatedsoclickingthe“Operations” dropdown will not display anything which is why we are going to create our own operation
– Clicktheslidertochangeitfromviewtoadd
– Thisallowsyoutospecifyanumberofoptionsinordertoconfigureyour operation successfully

IMG

– IwillnameourOperationTestbutagainyoucannameitwhateveryou want
– ClickBasicOptionsandwewilldiscusswhatitprovidesus

IMG

– Thefirstdropdownsetsyourgroupandbydefaultallagentsareadded to the “red” group which is what I have selected
– Theseconddropdownsetstheprofileyouwouldlikethisoperationto run. I have selected the Test profile I created earlier
– Thethirddropdownsetstheoptiontoclosethisoperationorleaveit open for future execution. I have set this to auto close since this is a lab
– Thelastdropdownsetstheoperationtorunimmediatelyafterstartingor pausing for you to inspect it. I have set it run immediately
– NowclickBasicOptionstocloseitandclickAutonomous

IMG

– Thefirstdropdownsetstheoperationtorunautonomouslyormanually with approval of each TTP executed
– Theseconddropdownsetswhichplanneryouwillutilizetoexecutethe operation. A planner is a module within CALDERA which contains logic for
–
how a running operation should make decisions about which abilities to use and in what order
– Thefinaldropdownsetsthefactsyouwilluseduringtheoperation.A fact is an identifiable piece of information about a given computer. Facts are directly related to variables, which can be used inside abilities
– NowclickAutonomoustocloseitandclickonStealth

IMG

– Theonlydropdownhereallowsforyoutoselectanumberofobfuscation techniques to obscure the commands you run on the host system
– Thesecondfieldsetsthejittervalue.Agentsnormallycheckinwith CALDERA every 60 seconds. Once they realize they are part of an active operation, agents will start checking in according to the jitter time, which is by default 2/8. This fraction tells the agents that they should pause between 2 and 8 seconds (picked at random each time an agent checks in) before using the next ability
– Thevisibilitysliderletsyousethowstealthyyouroperationwillremain. How visible should the operation be to the defense. Defaults to 51 because each ability defaults to a visibility of 50. Abilities with a higher visibility than the operation visibility will be skipped
– ClickStealthtocloseit
– Don’tclickSchedule.Scheduleallowsyouschedulethisoperationfora later date which we will not be doing
– Nowclickstarttobeginyouroperationandselectincludeagentoutput

IMG

– ThereisalotherebutIthinkmuchofitisselfexplanatory
– Thefirstareatonoteistheabilityatthetopofthescreentostop,pause, play, and skip the operation
– Thenexttotheseoptionsistheabilityatanytimetoswitchyour operation from a autonomous operation to a manual one
– NowwecanseethatourDiscoverSystemServicesabilitywasexecuted on the host and since we enabled the inclusion of agent output if we can
–
click the star at the end of the ability line we should be able to see the output from the command

IMG

– Clickthexinthetoprightcornertoreturntotheoperationscreen
– Congratulations!!Youhavesuccessfullydeployedanagent,createdan adversary profile, created an operation and run that profile against a host.
– Nowletscleanup

## Clean Up

– Nownormallyyoumightwanttosavealloperationsandprofilesyou create but in this instance I figure I’d show you how to get rid of them so you can start fresh
– Firstwewilldeletethisoperation.Goaheadandclickthegreendelete button located under download report which will revert your screen back to the original operations screen
– Nextlickthexinthetopleftcorneroftheoperationstabtoremoveit from your interface
– Youshouldnowbeontheprofilestabwhichyoucandothesamething in. Click the green delete profile button, click ok and then the red x in the
–
top left hand corner
– Nowforthefinalpieceletskillouragentandremoveitfromtheagents tab
– ClickthegreenagentPIDandselectkillagentthenselectok
– WaitfortheagentPIDtoturnredorrefreshtheCalderabrowsertaband go back to the agents tab. This may take a minute or two depending on the agents configuration
– Oncetheagentshowsasterminatedclicktheredxattheendofitto remove it from your view and you are all cleaned up....aside from one thing. The windows box.
– Ifyouwanttoensureacleanwindowsboxyoucanusethestationctl management menu to perform a soft reset and revert the windows box back to a clean instance taken upon deployment


## Thrunting

– Now lets switch overtoourKibanabrowsertabandgointotheDiscover tab within Kibana selecting the logs-* index

IMG

– The best way to view the activity we conducted on our host is to filter down the data to just want we want to see in this case I want to see process creation events and I want to display the user, parent process name, executing process name and command line.

– Since the agent we used was named "Splunkd", filtering down the wanted activity will be easy.

IMG

- Let's explain what's been done here: I've filtered the data set using the winlog channel field which contains the different event subscriptions we have available to us. Since we want a specific windows event ID, I chose the Security channel.

– I then wanted to specify the process creation event id of 4688, which I did by utilizing the event.code field.

– Lastly, I knew the name of my implant was Splunkd so I filtered on the parent process name field to specify the Splunkd process name

– To view the specific fields I wanted to see, I can simply search for the field names on the left hand side and added them to my table

– As you can see, we have this Splunkd.exe spawning Powershell.exe as the user vagrant on the windows10 host to run the Get-Service command

– There are a number of different detections we could write for this, but that is a lab for another day.


> Hopefully this lab helped you gain a basic understand of Caldera, how a C2 framework works and how to hunt the activity Caldera conducts using Kibana.