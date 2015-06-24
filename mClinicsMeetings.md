# Meeting Aug 23, 2012 #

Attending: Nyoman Ribeka, Sam Mbugua, Martin Were

- Discussed **Database** issues around clinic:
Tables: Patient, forms, observations

**Patient**
- Patient attributes, and identifiers configuration to be done on server side.
- We will have patient attributes and patient identifier tables on phone side.  Specifics of address to come later.

**Forms** No need to change the forms table, from the way it is defined in the current clinic.
Note: How to handle different versions of forms (e.g. checksum on a form) to potentially be done in the future.

**Cohorts & Obs**
- We need to remove the reporting and reporting compatibility module
- Under Cohort, we are keeping Cohort ID, Cohort Name.

**Obs Table**
Patient ID, Data type, Value Text, Value Numeric, Value Int, Field Name, Encounter Date

No concept or uuid's at this point. Maybe in the future.

- Will merge Value Numeric and Value Int in Obs Table
- Rename 'Field Name' to 'Observation Name' in Obs Table
- Rename 'Encounter Date' to 'Observation Date' in Obs Table

Will need to eventually think about complex obs.

**User Table**
Use case: on start of clinic, users will be downloaded onto the phone. These will be the users allowed to use the phone.

Still need to decide who will be downloaded.

Table should contain
- User ID (Primary Key), System ID (e.g. OpenMRS-ID), User Name (e.g. mwere), password, salt, status



TO DO:
[ ] Win to help determine how to make the mClinic site closed (with Sam's help) - by Monday next week.<br>
[ ] Who will remove the reporting compatibility module? (Sam - working on the merged module currently - 2 weeks)<br>
[ ] Someone to create the data model on phone - visual data model (Win to do it - visual - use mySQL to design table, do visual, and transform <br>
[ ] Will merge Value Numeric and Value Int in Obs Table  - Win (Wed) <br>
[ ] Rename 'Field Name' to 'Observation Name' in Obs Table - Win (Wed) <br>
[ ] Rename 'Encounter Date' to 'Observation Date' in Obs Table - Win (Wed) <br>
[ ] Martin and Judy to decide  on how complex obs will be displayed / Sam & Win on the backend side - far in the future<br>
[ ] Create User Table - Win (Wed)<br>


<h1>Meeting Sep 20th, 2012</h1>
Attending: Judy Wawira, Nyoman Ribeka, Sam Mbugua, Martin Were<br>
<ul><li>Changing the name to 'mUZIMA' from 'mClinic' given that mClinic was previously used by MVP<br>
</li><li>Judy will assume the role of project coordinator<br>
</li><li>Base system Android 2.1, and 3.0 (for tablets). Any older versions are ignored.<br>
</li><li>Licensing issues<br>
<ol><li>We need a license soon : <a href='http://en.wikipedia.org/wiki/Comparison_of_free_and_open-source_software_licenses'>http://en.wikipedia.org/wiki/Comparison_of_free_and_open-source_software_licenses</a>
</li></ol></li><li>Test server issues:<br>
<ol><li>Current test site is at  <a href='http://54.243.229.120:8080/openmrs/index.htm'>http://54.243.229.120:8080/openmrs/index.htm</a>
</li><li>Win to be given privileges to manage it in the US.<br>
</li><li>There will be a second test site. Win and Martin to set this up once they are back in the U.S.<br>
</li><li>One of the test servers will be for end users use to test, and another that developers use to test.</li></ol></li></ul>

Test Devices (already ordered):<br>
<ol><li>Samsung Galaxy Tab 32GB, Wi-Fi + 3G (Unlocked), 10.1 in – Black<br>
</li><li>Huawei Media Pad 7 inch (might need to buy in Kenya)<br>
</li><li>Google Nexus 7 (Unlocked)<br>
</li><li>Samsung Galaxy Tab2 7 inch Tablet - Silver (8GB, 3G) (Unlocked)<br>
</li><li>Ideos 8150 phone from Safaricom  – might have to buy in Kenya<br>
</li><li>Sony Ericsson Xperia Ray – might have to buy from Kenya<br>
</li><li>Want something up in about a month. Have a baseline apps before 2013.<br>
</li><li>Standing meetings with be Tuesdays 8 pm EAT (7pm or noon EST) - we will use FreeConferencing: +1 (559) 726 1200 + 429502</li></ol>

<ul><li>Win suggests that we need a good UI person<br>
</li><li>Data Structure (Table)<br>
</li><li>Form - Need to add md5/hash value in the forms table<br>
<blockquote>- Need to add flag to the form table for disable form (unused form)<br>
</blockquote></li><li>Sequences: this is an xform that has the  sequence.<br>
</li><li>Observation Table:<br>
<ol><li>Will change obs_datetime to DATE<br>
</li><li>Add Observation_Group (INT) FK to Obs_ID<br>
</li><li>Adding UUID</li></ol></li></ul>

<blockquote>Louis' Functionality to Incorporate<br>
</blockquote><ol><li>Device admin<br>
</li><li>Security<br>
</li><li>User Interface<br>
</li><li>Some workflow considerations</li></ol>

TO DO:<br>
[ ] Create timeline for the different things<br>
[ ] Find a UI person - and potentially do it as part of the development<br>
[ ] Fast track having a license - Win to look into that / Judy to ask Mike<br>
[ ] Win to get privileges to get new test site<br>
[ ] Create next site on Amazon when me and Win get to it<br>
[ ] Need to buy Samsung Galaxy Pocket - Martin to look at buying<br>
[ ] Judy to help with documenting Louis code<br>
TODO Data Model:<br>
[ ] Add md5 / hash value in the form table<br>
[ ] Add flag to the form table for disabled form (unused form)<br>
[ ] Win to add <br>

<h1>Meeting Oct 2, 2012</h1>
Attending: Judy Wawira, Nyoman Ribeka, Sam Mbugua, Martin Were<br>
<br>
- <b>API</b> is in the mClinic Repo, but Win says he is going through new technology to layer database to API. Win looking at:<br>
<ol><li><a href='http://greendao-orm.com/'>http://greendao-orm.com/</a>
</li><li><a href='http://ormlite.com/'>http://ormlite.com/</a>
We will go with ORM LIte</li></ol>

- <b>Technology Stack</b>
<blockquote><a href='.md'>Database &lt;--&gt; ORM Lite &lt;--&gt; DAO &lt;--&gt; Service </a> = <a href='.md'>API </a></blockquote>

- <b>Consumer Stack</b>
<blockquote><a href='.md'>API </a> <br>
<br>
<--><br>
<br>
 <a href='.md'>Business Logic &lt;--&gt; Android "Native Apps or Web HTML 5" </a> = <a href='.md'>Consumer </a></blockquote>

-<b>View</b>
<ol><li><a href='http://code.google.com/p/roboguice/'>http://code.google.com/p/roboguice/</a>
</li><li><a href='https://github.com/excilys/androidannotations/wiki/Cookbook'>https://github.com/excilys/androidannotations/wiki/Cookbook</a>
</li><li><a href='http://code.google.com/p/google-guice/'>http://code.google.com/p/google-guice/</a>
</li><li><a href='http://www.springsource.org/spring-android'>http://www.springsource.org/spring-android</a></li></ol>

<blockquote>- Win and Sam to work primarily on the API side of things. The key is to ensure that the APIs are standardized. <br>
- Judy got someone to work on Android. <br>
- Martin introduced Evan Blank (Mt. Sinai Med student) to Judy. <br>
-Device Management / Security should be different APKs. <br>
-Connect Louis' Client UI to the API - that was the agreement. <br></blockquote>

<b>Timelines:</b> <br>
- By  Friday - Service Description -  business / view interacting with databases. <br>
- Within two weeks - first API release (will have encrypted database, ORM Lite, DAOs). <br>
- Two weeks later - plug Louis' UI to API. <br>
- 6 weeks to have a release (Mid-November).  Will also include the security features and device management features. <br>

TO DO <br>
[ ] Judy to document wishlist. <br>
[ ] Sam to create bullets for MVP. <br>
[ ] Win to tell Martin about the second test site. <br>
[ ] Martin to follow up on devices. <br>

<h1>Meeting 9th October 2012</h1>
In attendance: Sam, Judy, Martin <br>

<b>Agenda:</b> <br>
> Update on services of clinic (Portion marked for completion by last week)<br>
> Update on API (Still a concept)<br>
> Update on documentation ( MVP functionality/ New software architecture / Louis ) <br>
> General Project management in preparation for release (Web hosting/ mailing lists etc)<br>
> Plan for the next week's work <br>
> AOB <br>

<b>Services:</b> Not present as of today.<br>
<br>
<b>Proposed System Architecture By Win</b> <br>
> Review of Win's email suggestion <br>
> Advantages of NoSQL :<br>
<ol><li>faster indexing/search<br>
</li><li>Protect users from complexities of Openmrs<br>
</li><li>Easy to port to other new uses.<br>
> Previous opinion was to move from SQLLite.<br>
> Big shift from SQLLite after Oracle took over SQL   <br>
> What is an observer(in relation to WS)? Similar to a listener. <br>
> How well does Lucene work with LevelDb/PouchDB? <br>
> How well does the database work for encryption?<br>
> How well can it work in cross platform settings?<br>
> How does sync work with NoSQL? <br>
> How to abstract ourselves from dependencies within OpenMRS <br>
> System has to talk to DHIS, and system has to talk to RedCap (New wishlist items).<br>
</li></ol><ul><li>These are potential student or side projects that are of priority.<br>
> How do we incorporate feedback from key experts like Burke?<br>
<ol><li>Win / Martin to reach out to him.<br>
</li><li>Judy to email Burke updates<br>
> Sam to review the use of NoSQL database, data encryption on device and merging this to a service. (By Friday to send out an email)<br><br></li></ol></li></ul>

<b>Documentation:</b> <br>
> Sam on MVP: To look for some time to do documentation.<br>
> Louis: Just to email Win on the updates?<br>
<ul><li>We plan to reuse what is not pegged on the database</li></ul>

<b>General Project Management</b>
<ul><li>Aim to have a new timeline by the weekend (By Sunday to have a revised timeline)</li></ul>

> When to engage students and the open source community?<br>
<ul><li>Core to work on first release<br>
</li><li>Students to start on side projects when ready</li></ul>

<b>Device Management:</b>
<blockquote>> Should go hand in hand with the main  application development <br>
> To discuss next week on what are the desired features/ correlate what Louis is able to do  and what additional  features are required.<br>
> Summary of Device management functionality include <br>
- Limit programs can run on the device <br>
- Remote wipe <br>
- Encryption on mobile device (this should be part of core app) <br>
- SMS to ping device <br>
- Warning messsages remotely <br>
- GPS-based disabling functionility <br>
- Automatic malware/antivirus updates <br>
- Scheduled antivirus / malaware application. <br>
- Quick install and remote install functionality <br>
- Secure data transmission <br>
- Server based authentication of user the first time <br>
- Securing database for the applications <br>
- Tracking Airtime used for data transmission / download <br>
- Allow multiple users per device. <br></blockquote>

<b>What others have Done on Device Management</b> <br>
> We could adopt similar functionality like in these apps: <br>
# Lock stuff down: <a href='https://play.google.com/store/apps/details?id=com.carrotapp.protectpronew'>https://play.google.com/store/apps/details?id=com.carrotapp.protectpronew</a> <br>
# Do stuff based on location: <a href='https://play.google.com/store/apps/details?id=com.twofortyfouram.locale'>https://play.google.com/store/apps/details?id=com.twofortyfouram.locale</a> <br>
# Do stuff: <a href='https://play.google.com/store/apps/details?id=net.dinglisch.android.taskerm'>https://play.google.com/store/apps/details?id=net.dinglisch.android.taskerm</a>

<b>TO DO</b> <br>
[ ] Create a page for Core Device Management/ Wishlist <br>
[ ] Devices - Samsung Galaxy Pocket as one of the devices to get.<br>
[ ] Martin to read and edit the wishlist :  <a href='http://code.google.com/p/mclinic/w/edit/Wishlist'>http://code.google.com/p/mclinic/w/edit/Wishlist</a> <br>
[ ] what  is the NoSQL database to use? LevelDB/PouchDB<br>
<blockquote>References: <a href='http://vschart.com/compare/leveldb/vs/couchdb'>http://vschart.com/compare/leveldb/vs/couchdb</a>