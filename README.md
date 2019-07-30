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
6. The "C:\RMS\project files" folder contains Ignition projects "rms_2019-07-30_2120.zip" and "rms_project_2019-07-30_2300_partial.proj" for Ignition version 8 and 7.9.10 respectively. Create project named "rms" in your Ignition version and import appropriate project into it.
7. Start the Ignition server and open the designer and set the "StartPubNub" tag and "StartTimer" tag to true one by one in that sequence.If these tags don't exist in Ignition db, then import tags from "C:\rms\project_files\tags.xml" in the project.
8. open the wrapper.log file of Ignition and see that pubnub and timer have started successfully without any exceptions.(If you get errors such as "pubnub not found" in PubNubScripts file, then stop and restart the Ignition gateway and try again. This is particularly observed in Ignition version 8).
9. right click and open the all.html file in a browser (chrome preferred) and it will display the configured dash boards.
10 right click open the states.html in a new tab in browser (chrome preferred) it will display the tag values which can be updated manually or set to update automatically every 5 seconds. The number of rows per page can be changed with parameter maxpage (default 10) in C:\RMS\states.html file.
11. In order to view dash boards and states in a android phone or iPhone, copy the files from main folder C:\RMS (exclude subfolder) using usb cable. The Android file transfer is quite streight forward (drag and drop) but for iPhone use instructions give in https://www.maketecheasier.com/how-to-copy-files-tofrom-your-iphone/ . 
12. You can passowrd protect the folder on iPhone using the file manager downloaded in above step.
13. To open html file in a borwser in Android, you have to download a free app "open in browser".
========= Geo Location tracking (THIS MODULE IS SUSPENDED TEMPORARILY, FILES GLS.HTML AND GLC.HTML ARE DELETED) ============
14. New files gls.html, gls.js, glc,html, glc.js, users.txt, profiles.txt and new project rms_project_2019-05-27_2310_partial.proj added to include new scripts for geo location tracking and some bug fixes added.
15. The downloaded zip file will contain the above new files. Extract the files and copy them under C:/rms as given in step 1 above.
16. Modify the config.js to add pubnub keys and modify the gls.html and glc.html files to add the google maps API keys as explained in https://www.pubnub.com/tutorials/javascript/mapping-javascript-tracking/
17. Start PubNub as explained in step 7 above. The tmer needs to be started only if you are using EON DashBoards. For GLS its not required.
18. Open gls.html in a HTML5 browser (chrome preferred) on Ignition server, and glc.html on client machine or Mobile phone. (you need to copy glc.html, glc.js and config.js on the mobile phone (android or ios) as explained in step 11. 
19. Set simulate=false in config.js file and restart gls.html and glc.html to view real geolocation not simulated one.
20. The users.txt and profiles.txt are json files for users and password data and profiles data respectively. By default 3 users are defined (admin, guest, visitor with password and password,gues and visitor). Add any number of users and profiles ad you want for your projects.
=================== PubNub Remote Web Service (PRWS) files =============================
21. This module is like RWS (Restful Web Servies of AR SCADA) module but it uses PubNub instead of webDev for viewing Ignition data on an HTML page. The GitHub repository includes three new files (1) prws.js (2) prws.html and (3) prws1.html in the C:\RMS folder and two new projects (1) rms_project_2019-07-30_2300_partial.proj for Ignition version 7.9.10 and (2) rms_2019-07-30_2120.zip for Ignition version 8. A few files such as config.js , states.html and states.js have been modified.
22. Execute steps 1 to 8 above for RMS module, except that in step 7 set only StartPubNub tag not the StartTimer flag.
23. right click prws1.html file and open it it chrome browser and you will the the HTML page with charts. Similarly open prws.html in chrome to see the simplified HTML page.
24. Right click the states.html page and open it in chrome browser to see the states of all configured tags in tags.txt file. This page is same as defined in step 10 above and it runs without the timer flag set.
25 You can now set the StartTimer flag to true in Ignition to see the EON Dash boards as explained in step 9 above.
