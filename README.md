# RMSCADA
RMSCADA download of evaluation version.
Steps for installing and runing RM SCADA under Ignition:

1. Download the RMS-master.zip from www.github.com/pramanj/rmscada. Unzip and copy files under "C:\RMS" folder on windows machine.
2. The main folder "C:\RMS" contains subfolder "project files" containing backup of trial version and the main folder contains following main files that you have to configure for our project:
2.1 tags.txt - contains tag data base in json format that is updated from Ignition every cycle for tag values.
2.2 eon.txt - contains the dash board parameters (in json format) to be displayed by RMSCADA.
2.3 config.js - contains the pub/sub keys of PubNub that you have to obtain from PubNub portal.
2.4 all.html and states.html files that display the dash boards and tag values in an HTML5 page under a browser.
3. copy the pubnub's jar file "pubnub-gson-4.22.0-beta-all.jar" kept under path "C:\RMS\project files" of the downloaded unzipped file to ignition's lib\core\gateway folder e.g. "C:\Program Files\Inductive Automation\Ignition\lib\core\gateway".
4. create an account in www.PubNub.com portal for youself and create pub/sub keys for use in RMS project (enable history on them on PubNub ).
5. open the file "C:\RMS\config.js" using notepad++ editor and replace the "demo" string with pub/sub keys obtained from PubNub.
6. The "C:\RMS\project files" folder contains Ignition projects "rms_2019-04-08_1913.zip" and "rms_project_2019-05-20_1108_partial.proj" for Ignition version 8 and 7.9.10 respectively. Create project named "rms" in your Ignition version and import appropriate project into it.
7. Start the Ignition server and open the designer and set the "StartPubNub" tag and "StartTimer" tag to true one by one in that sequence.If these tags don't exist in Ignition db, then import tags from "C:\rms\project_files\tags.xml" in the project.
8. open the wrapper.log file of Ignition and see that pubnub and timer have started successfully without any exceptions.(If you get errors such as "pubnub not found" in PubNubScripts file, then stop and restart the Ignition gateway and try again. This is particularly observed in Ignition version 8).
9. right click and open the all.html file in a browser (chrome preferred) and it will display the configured dash boards.
10 right click open the states.html in a new tab in browser (chrome preferred) it will display the tag values which can be updated manually or set to update automatically every 5 seconds. The number of rows per page can be changed with parameter maxpage (default 10) in C:\RMS\states.html file.
11. In order to view dash boards and states in a android phone or iPhone, copy the files from main folder C:\RMS (exclude subfolder) using usb cable. The Android file transfer is quite streight forward (drag and drop) but for iPhone use instructions give in https://www.maketecheasier.com/how-to-copy-files-tofrom-your-iphone/ . 
12. You can passowrd protect the folder on iPhone using the file manager downloaded in above step.
13. To open html file in a borwser in Android, you have to download a free app "open in browser".
