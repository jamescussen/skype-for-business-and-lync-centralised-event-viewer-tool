Skype for Business and Lync Centralised Event Viewer Tool
=========================================================

            

Event Viewer logs remain one of the best troubleshooting tools for Lync and Skype for Business servers. An enormous amount of useful information can be found in the Event Viewer Logs, which can then be used to either understand the current state of the system
 or do root cause analysis on prior issues. 


So I decided to build a simple tool that centrally displays all of the Event Logs from Lync or Skype for Business servers or pools within an environment. This allows for a fast one-stop-shop for triaging issues across multiple Lync/Skype for Business servers
 in your environment. This can be especially handy for easily correlating problems that might have occurred across multiple servers in a pool.


 


![Image](https://github.com/jamescussen/skype-for-business-and-lync-centralised-event-viewer-tool/raw/master/eventlogtool1.00_sm.png)


 


**Features:**


 


  *  Start and End Time – You can select Start and End date and time for events
(yy/mm/dd hh:mm format). This can be particularly handy if you know the approximate time that an issue occurred on the system.

  *  Server – Select specific servers or entire pools for which you would like to see the Events Logs. By default all Lync Front End servers are selected (ie. “ALL FRONTENDS”).

  *  Event level selection – Select if you want to see Critical, Error, Warning, and Information event messages.

  *  EventID Include/Exclude – By default, these fields can be left blank. However, you can select to either include or exclude specific event numbers when you get events. These fields accept Regular Expression formatting. For example,
  if you entered “^5”, you will get all events that start with “5” , or you could get specific multiple events using '|' like this “31147|31202”, or your could get a range of events using '[]' like this '620[0-9][0-9]'.

  *  Find Next / Previous – You can jump forward or backwards through the event list. The find feature checks all cells in each row against the text in the find text box (this is based on regular expression). If you don't put any text in the
 find textbox the find next and previous buttons can also be used to step through each event in the list.

  *  The Get Events button will start the process of getting the specified events from the selected servers.

  *  Web Search! – Often the easiest method to find more information on events is to search on the web for them. So the tool gives you the option to Google, Bing, Duck Duck Go or search TechNet Forums for more information.

  *  View Event - This button will open a window with the event in larger text box. This helps in some cases when the event message text will not fit within a row in the main window.

  *  The Copy button will copy the selected row to the clipboard so you can paste it somewhere, like an email for example.

  *  Export Statistics to CSV – The Export Stats button will export per event counts to a CSV file. This will quickly allow you to see which events have been occurring more than others.

  *  Export Events to CSV – You may want to have record of these 'momentous' events for future reference.


**1.01 Small Update**


  *  Added standalone mediation servers to the list. 

**1.02 The Greig Request Update (15/7/2018)**


  *  Added options for searching 'ALL FRONTENDS', 'ALL FRONTENDS and SBAs', and 'ALL SBAs'.

  *  Added improved performance (2x-3x improvement) of 'Include Event ID' filtering when '41024,41033' format is used (Note, only works for Include and
**not** Exclude Event ID). Using server side filtering for this improvement (also saves CPU cycles on client machine).


 


**Tool Requirements**


The Centralised Event Viewer Tool must be run on a server with the Lync / Skype for Business module installed on it (as it uses Powershell commands to find the Lync/Skype4B pool information). This would usually be a front end server in the pool. The tool
 is capable of listing large numbers of events (tens-of-thousands of events), however, getting large numbers of events can take a while to process. The tool will process 1000 events in approximately 2 seconds (this scales fairly linearly). As a rule though
 it’s usually best to keep searches under a month in length so that the number of events don’t become problematic.


You must enable “**Remote Event Log Management (RPC)**” on all of your Lync/Skype for Business servers Windows firewalls in order to access these logs from the central server running the tool. This rule is already pre-populated in
 the Windows Firewall Advanced setting rules. So you simply need to Enabled the rule as shown below:


**Open Firewall on all Lync / Skype for Business Servers:**





![Image](https://github.com/jamescussen/skype-for-business-and-lync-centralised-event-viewer-tool/raw/master/firewall-rule-required_sm.png)


 


This is a dynamic service rule that opens the required ports automatically. However, the ports that get used in practice are port
**TCP 135 (RPC)** and port **TCP 49153 (Remote Event Log)**. These firewall rules will become more important if you are trying to connect to Edge servers from an internal server, as the firewall between the servers will need to allow
 these ports.


Once this has been set on the servers that you are getting event logs from, you are set to go!


 


**Full post available here: [http://www.myskypelab.com/2016/07/Centralised-Event-Viewer-Tool.html](http://www.myskypelab.com/2016/07/Centralised-Event-Viewer-Tool.html)**





        
    
