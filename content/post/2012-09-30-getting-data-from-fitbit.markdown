---
author: andy
comments: true
date: 2012-09-30 23:16:36+00:00
layout: post
link: http://citizen-statistician.org/2012/09/30/getting-data-from-fitbit/
slug: getting-data-from-fitbit
title: Getting Data from FitBit
wordpress_id: 27
categories:
- Data
---

Getting data out of a FitBit, as Rob pointed out, is not as easy as simply clicking an export button on the FitBit website. Fortunately, FitBit released their API to developers in February and since then a few solutions of obtaining the raw data have been realized. John McLaughlin has written an [open source script](https://github.com/loghound/Fitbit-for-Google-App-Script) (available on GitHub) that enables FitBit users to download their data into a Google spreadsheet.

[Ernesto Ramirez](http://vimeo.com/user1994782) (a Community Organizer for Quantified Self) has put together a tutorial on [Vimeo](http://vimeo.com/) for [Importing FitBit data into Google Spreadsheets](http://vimeo.com/26338767). His directions are also printed below.

http://vimeo.com/26338767

**How to set up FitBit & Google Spreadsheets integration:**



	
  1. Download the FitBit For Google Apps Script from Github

	
    * Open the [Github repository for the script](https://github.com/loghound/Fitbit-for-Google-App-Script)

	
    * Click the downloads button and save the .zip file to your computer.

	
    * Unzip the folder and open the _fitbit.js_ file in a text editor.




	
  2. Set up your FitBit Developer account and register an app.

	
    * Go to [dev.fitbit.com](http://dev.fitbit.com/) and sign in using your FitBit login information.

	
    * Click on the “Register an App” at the top right corner of the page.

	
    * Fill in you application information. You can call it what you want. Make sure to click “Browser” for the Application Type and “Read Only” for the Default Access type fields. (Note: The URL fields are required. These can be your personal website, etc. They aren't that important to using this script, but are needed to register an application.)

	
    * Read the terms of service and if you agree check the box and click “Register”




	
  3. Record the API keys

	
    * Copy the Consumer Key

	
    * Copy the Consumer Secret

	
    * You can save these to a text file, but they are also available anytime you return to dev.fitbit.com by clicking on the “Manage my Apps” tab.




	
  4. Set up Google Spreadsheet Script

	
    * Create a new google spreadsheet.

	
    * Go to `Tools->Script Editor`

	
    * Replace the template with_ fitbit.js _(copy the entire thing from your text editor and paste it into the template)

	
    * Save the script and name it.

	
    * Click the "Select Function" button menu and choose “renderFitbitConfigurationDialog”. Run the script by clicking the play button.

	
    * Run the “renderFitbitConfigurationDialog” function again. In your spreadsheet window, enter your consumer key and consumer secret in the dialog box.

	
    * Select “Authorize” from the "Select Function" button menu and run the script.

	
    * Enter your FitBit user name and password in the dialog box.

	
    * Select the ‘refreshTimeSeries” function and run it to get your data. (Note: If you get the following error: _TypeError: Cannot call method “getContentText” of undefined. (line 77), _ select and run the "renderFitbitConfigurationDialog" function, making sure to select one or multiple items in the Loggables list box.)





You can also set up an automatic trigger to update your spreadsheet automatically with new data. To do this:

	
  * Go to `Tools-> Script Editor`

	
  * Go to the “Trigger” menu and select ‘current scripts triggers’

	
  * Add a new trigger that runs ‘refreshTimeSeries’ that is ‘time driven’ and choose an interval for the spreadsheet to update (e.g., ‘hour timer’ updates the spreadsheet ‘hourly’).

	
  * Click save.


