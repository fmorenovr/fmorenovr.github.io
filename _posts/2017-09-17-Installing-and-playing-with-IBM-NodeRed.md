---
layout: post
title:  "Installing and playing with IBM NodeRed and implementation with Bluemix and Watson."
subtitle: Here you'll learn to setup node-red on IBM cloud platform and integrate with Watson API.
date:   2017-09-17 00:25:12 -0500
categories: IDEs
---
# Node Red

Node-RED is a programming tool to connect hardware devices, APIs and online services in a simple mode.  
It's provide through a browser server.  
You can install write in bash:

    sudo apt-get install -g node-red

And start a project writing:

    sudo node-red dendrobytes.json

# Components

Packages that can help you to develop faster and easier.

## Dashboard

Allow you to create a dashboard (with charts, tabs, menus, etc).

    sudo npm install -g node-red-dashboard

## Sample

Create a simple dashboard with different data and charts.

Here shows node-red example:

![localhost][node-example]

And here, the respective dashboard:

![dashboard][node-dashboard]

## https

Allow you to create HTTPS services.

    sudo npm -g install node-red-contrib-https

## To set up https

include ca, key and crt files using *fs* on file `settings.js` and create a `tls-ssl/` folder and put the files there.

## Implementing with IBM-Bluemix IoT platform

Firts, you must register on [bluemix-console](https://console.bluemix.net/).

![register][bluemix-register]

Once created your account, you should create an organization, I prefer fmorenovr in US South.  

![organization][bluemix-organization]

Then, choose an apropiate name-space:

![space][bluemix-space]

And confirm.

![summary][bluemix-summary]

Then, go to catalog and choose in Boilerplates tab.

![catalog][bluemix-catalog]

Next, choose "Internet of Things Platform Starter".  You'll see this view.

![iot-platform][bluemix-iotplatform]

Then, create a Cloud Foundry App:

![foundryApp][bluemix-foundryApp]

Wait for connect and run ...

![foundryApp-run][bluemix-foundryAppRun]

You can verify your information in "dashboard" tab.

![dashboard-tap][bluemix-dashboardTab]

Press on "Internet of Thing Platform", this shows info of Iot Instance:

![iot-service][bluemix-iotservice]

Click on `launch` and redirects to Watson IoT Platform:

![watson-paltform][bluemix-watsonPlatform]

Once here, we must create a device type, go to Device tab:

![watson-device-type-1][bluemix-watsonDevice-Type-1]

Click on +Add Device:

![watson-device-type-2][bluemix-watsonDevice-Type-2]

Select Manufacturer and model, and then finish.

![watson-device-type-2][bluemix-watsonDevice-Type-3]

Next, create a Device with a device type created.

![watson-device-device-1][bluemix-watsonDevice-Device-1]

Add a token and finish.

![watson-device-device-2][bluemix-watsonDevice-Device-2]

Then, you will have a summary of your new Device:

![watson-device-device-3][bluemix-watsonDevice-Device-3]

You can verify in Devices:

![watson-device-device-4][bluemix-watsonDevice-Device-4]

Second, generate API Key in APP tab, just press on Generate API Key:

![watson-api-key-1][bluemix-watsonAPIKey-1]

Verify then:

![watson-api-key-2][bluemix-watsonAPIKey-2]

Once created, go to our IoT platform, in this case is [Jenazads-ibm.mybluemix.net](http://jenazads-ibm.mybluemix.net).  
Make a security settings (create an username and password) and go to node-red.  

![nodered-security][bluemix-noderedSecurity]

Go to the node-red page:

![nodered-secure][bluemix-noderedSecure]

Authentificate ...

![nodered-login][bluemix-noderedLogin]

And have fun :D

![nodered-tool][bluemix-noderedTool]

### Example connection ibm-iot module

You need a basic information, an API key and API key token generate (if you don't remember, you should generate a new API key).

![node-bluemix-iot][bluemix-noderedIBMConnect]


## Implementing Watson with NodeJS

Finally, we use Watson !!, First of all, download watson package to node-red:

    sudo npm install -g node-red-contrib-ibm-watson-iot

Or, through node-red tool, in right-side menu -> Manage palette -> Pallette -> Install -> search package and install.

![nodered-tool-install][bluemix-noderedInstall]

Then, we try connection (your organization is your Watson IoT url):

![nodered-tool-watsoniot][bluemix-noderedWatsonConnect]


[node-example]:                   /assets/tools/node-red/node_1.png
[node-dashboard]:                 /assets/tools/node-red/node_2.png
[bluemix-register]:               /assets/internet_services/Bluemix/ibm_1.png
[bluemix-organization]:           /assets/internet_services/Bluemix/ibm_2.png
[bluemix-space]:                  /assets/internet_services/Bluemix/ibm_3.png
[bluemix-summary]:                /assets/internet_services/Bluemix/ibm_4.png
[bluemix-catalog]:                /assets/internet_services/Bluemix/ibm_5.png
[bluemix-iotplatform]:            /assets/internet_services/Bluemix/ibm_6.png
[bluemix-foundryApp]:             /assets/internet_services/Bluemix/ibm_7.png
[bluemix-foundryAppRun]:          /assets/internet_services/Bluemix/ibm_8.png
[bluemix-dashboardTab]:           /assets/internet_services/Bluemix/ibm_9.png
[bluemix-iotservice]:             /assets/internet_services/Bluemix/ibm_10.png
[bluemix-watsonPlatform]:         /assets/internet_services/Bluemix/ibm_11.png
[bluemix-watsonDevice-Type-1]:    /assets/internet_services/Bluemix/ibm_12.png
[bluemix-watsonDevice-Type-2]:    /assets/internet_services/Bluemix/ibm_13.png
[bluemix-watsonDevice-Type-3]:    /assets/internet_services/Bluemix/ibm_14.png
[bluemix-watsonDevice-Device-1]:  /assets/internet_services/Bluemix/ibm_15.png
[bluemix-watsonDevice-Device-2]:  /assets/internet_services/Bluemix/ibm_16.png
[bluemix-watsonDevice-Device-3]:  /assets/internet_services/Bluemix/ibm_17.png
[bluemix-watsonDevice-Device-4]:  /assets/internet_services/Bluemix/ibm_18.png
[bluemix-watsonAPIKey-1]:         /assets/internet_services/Bluemix/ibm_19.png
[bluemix-watsonAPIKey-2]:         /assets/internet_services/Bluemix/ibm_20.png
[bluemix-noderedSecurity]:        /assets/tools/node-red/node-bluemix_1.png
[bluemix-noderedSecure]:          /assets/tools/node-red/node-bluemix_2.png
[bluemix-noderedLogin]:           /assets/tools/node-red/node-bluemix_3.png
[bluemix-noderedTool]:            /assets/tools/node-red/node-bluemix_4.png
[bluemix-noderedInstall]:         /assets/tools/node-red/node-bluemix_5.png
[bluemix-noderedIBMConnect]:      /assets/tools/node-red/node-bluemix_6.png
[bluemix-noderedWatsonConnect]:   /assets/tools/node-red/node-bluemix_7.png


