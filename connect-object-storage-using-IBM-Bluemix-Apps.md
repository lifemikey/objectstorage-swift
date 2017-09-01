---

copyright:
  years: 2017
lastupdated: "2017-07-11"

---
{:new_window: target="_blank"}
{:shortdesc: .shortdesc}

# Access Object Storage using IBM Bluemix Apps

## Apps

Limited storage size is an issue for all workloads. SoftLayer furnishes its customers cloud storage as Object Storage, which helps solve the problem for keeping static content in unlimited capacity. IBM provides Bluemix, a Platform as a Service (Paas) that offers a cost-effective cloud platform for developers to programmatically implement owned services. In this article we provide you with straightforward steps to leverage Object Storage (SoftLayer) through Node.JS (IBM Bluemix), assuming you have an active SoftLayer account and existing Object Storage deployed.

You will create a new Bluemix application, make some edits to connect existing Object Storage, and deploy the application in the cloud. Click [here](http://blog.softlayer.com/2015/softlayer-bluemix-and-openstack-powerful-combination) for more information on SoftLayer and Bluemix

## Register for an IBM ID and sign in to Bluemix

1.    Open a browser window and enter https://console.ng.bluemix.net/ to register for an IBM ID and sign in to Bluemix.

2.    Click the Get Started Free button and either click the Already have an IBM ID? or Log in links if you an ID or have already signed up for Bluemix.

If you do not have an ID, fill out the required fields on the Sign up for IBM Bluemix screen and click the **Create Account** button.


## Get started with Node.JS

 1.    Log in to bluemix.net with your ID; you should be at the Bluemix Dashboard.

 2.    Click the **Create App** button located in the top of the page in the Cloud Foundry Apps section.

 3.    Click **Web** in the **What kind of app are you creating?** window.

 4.    Select SDK for Node.js under How do you want to get started? <br/> 
 ![Figure 1: Select SDK for Node.js](/images/bluemix_fig1.png) <br/>
 After making your selection, you will see details about the runtime displayed at the bottom of the page along with a documentation link.

 5.    Click the **Continue** button.
 
 6.    Enter the name of your application in the **App Name** field. Give the app a unique name; a suggestion is to append your initials and or the date to the end of the name. Click **Finish**.
 ![Figure 2: Name your app](/images/bluemix_fig2.png)<br/>
 Your new Node.js app has been deployed to Bluemix when you see the Your app is running and its URL at the top of the screen.

 7.    Click **Overview** in the left navigation pane to see details about your app.
 ![Figure 3: Your app is running and its URL](/images/bluemix_fig3.png)

 8.    Click the **Add Git** button on the **Application Overview** page, which will generate a Git Repository that will be associated with your newly created Node.js application.
 ![Figure 4: Application Overview page](/images/bluemix_fig4.png) <br/>
 The Create Git Repository window will appear.

 9.    Validate that the Populate repo with the starter app… checkbox is selected so the Git Repository will be populated with the starter code and click **Continue**.
 
 10. Click **Close** once you receive the **Success!** message. You will have a new GIT URL associated with your application. It will appear under the app name and routes information.

 11. Click the **Edit Code** button, which will open a new browser tab and take you to the home page of the Git Repository you just created. <br/>  You are now inside IBM Bluemix DevOps Services. DevOps Services allows you to do a number of tasks associated with your Bluemix applications. These tasks include planning and tracking the development of your application, or creating stages and associated jobs for building and deploying your application. For our example, we will use the in-browser integrated development environment (IDE) within DevOps Services to edit and deploy the Node.js application to Bluemix.

 12. Click on package.json file in the left navigation window. <br/>  You will see the contents of package.json in the right side editor window. For this example, you will require an additional ssh node module dependency as part of your application; the package.json file needs to be updated accordingly. 
 
 13. Edit package.json to include the ssh dependency as shown in below. When you are done, your package.json file should look similar to this image. Adding ssh2 will install the new module via NPM when your application builds. <br/>
 ![Figure 5: package.json with ssh dependency](/images/bluemix_fig5.png) 

 14. Find your app.js file in the left navigation menu in order to include additional code to establish a connection to and read from your Object Storage. Add the code below after line 19, app.use, or copy and paste the code under. (You will input your credentials and host in a later step.) This new code will add a /slobj route to your application that  we will use to verify connection to the storage.  
 ![Figure 6: Edited code](/images/bluemix_fig6.png)
 
 ```
 app.get('/slobj', function(req, res){
      var Client = require('ssh2').Client;
      var conn = new Client();
      conn.on('ready', function() {
            console.log('Client :: ready');
            conn.sftp(function(err, sftp) {
                  if (err) throw err;
                  sftp.readdir('/', function(err, list) {
                        if (err) throw err;
                        console.dir(list);
                        result = list;
                        conn.end();
                        if(result.length>0){
                              var fname = '';
                              for(var i=0; i < result.length ; i++)
                                    fname = result[i].filename + ' , '+ fname;
                              res.send('SFTP connected : ' + fname);
                        }
                        else
                              res.send('SFTP not connected');
                  });
            });
      }).connect({
            host: '<YOUR_OBJ_STORAGE_HOST>',
            port: 22,  
            username: '<USER_NAME>',
            password: '<API_KEY>' });
 });
 ```
 
 15. Minimize the IBM DevOps Services window.

## Create Object Storage container on SoftLayer

 1.    Open a browser window, enter https://control.softlayer.com, and log in.

 2.    Select **Storage** > **Object Storage**. Find your device and click the **View Credentials** link. <br/>
 ![Figure 7: Account Credentials](/images/bluemix_fig7.png)
 
 3.    Make note of your **Username** and **API Key**.
 
 4.    Restore the IBM DevOps Services window and input your credentials (see screenshot in Step 14 above, lines 45, 47, and 48).  
        host: '<YOUR_OBJ_STORAGE_HOST>',
        username: '<USER_NAME>',
        password: '<API_KEY>'

 5.    Click the triangle in the IBM DevOps Services window to deploy your app. Click **OK** if you receive a message asking you to stop and redeploy your application. <br/>
 ![](/images/bluemix_fig8.2.png)

 6.    Open new browser window and enter http://<your_bluemix_app_url>/slobj, which will activate the new route we created in step 14 in your node.js application.

 This example code connects to the specified SoftLayer Object Storage, reads container names, and responds by rendering the container names in HTML at the route you have stated. <br/>
 ![Figure 8: Page results](/images/bluemix_fig8.png)
 ![Figure 9: Object Storage screen within SoftLayer](/images/bluemix_fig9.png)

 

