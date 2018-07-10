---

copyright:
  years: 2017, 2018
lastupdated: "2018-07-10"

---
{:note: .deprecated}
{:new_window: target="_blank"}


# Connecting to {{site.data.keyword.objectstorageshort}} OpenStack Swift by using {{site.data.keyword.Bluemix_notm}} Apps

**Apps**

Limited storage size is an issue for all workloads. {{site.data.keyword.BluSoftlayer}} furnishes its customers cloud storage as {{site.data.keyword.objectstorageshort}}, which helps solve the problem for keeping static content in unlimited capacity. IBM provides {{site.data.keyword.Bluemix}}, a Platform as a Service (PaaS) that offers a cost-effective cloud platform for developers to programmatically implement owned services. You can use {{site.data.keyword.objectstorageshort}} through Node.JS, assuming you have an active {{site.data.keyword.BluSoftlayer}} account and existing {{site.data.keyword.objectstorageshort}} deployed.

You can create a {{site.data.keyword.Bluemix_short}} application, make some edits to connect existing {{site.data.keyword.objectstorageshort}}, and deploy the application in the cloud. Click [here](http://blog.softlayer.com/2015/softlayer-bluemix-and-openstack-powerful-combination) for more information on {{site.data.keyword.BluSoftlayer}}.


## Registering for an {{site.data.keyword.appid_long_notm}} and Signing in to {{site.data.keyword.Bluemix_notm}}

1. Open a browser window and enter `https://console.ng.bluemix.net/` to register for an {{site.data.keyword.appid_long}} and sign in to {{site.data.keyword.Bluemix_short}}.

2. Click **Get Started Free** and either click **Already have an {{site.data.keyword.appid_long_notm}}**/**Log in**.
   - If you don't have an ID, complete the required fields on the Sign-up screen and click **Create Account**.


## Getting started with Node.JS

 1. Log in to bluemix.net with your {{site.data.keyword.appid_long_notm}}.

 2. Click **Create App** in the Cloud Foundry Apps section.

 3. Click **Web** in the **What kind of app are you creating?** window.

 4. Select SDK for Node.js under **How do you want to get started?**<br/> 
    ![Figure 1. Select SDK for Node.js](/images/bluemix_fig1.png)<br/>
    After you made your selection, you can see details about the runtime that is displayed on the page along with a documentation link.

 5. Click **Continue**.
 
 6. Enter the name of your application in the **App Name** field. Give the app a unique name. For example, you can append your initials or the date to the end of the name. Click **Finish**.
    ![Figure 2. Name your app](/images/bluemix_fig2.png)<br/>
    Your new `Node.js` app is deployed to {{site.data.keyword.Bluemix_short}} when you see the "Your app is running" message and its URL on the screen.

 7. Click **Overview** in the left navigation pane to see details about your app.
 ![Figure 3. Your app is running and its URL](/images/bluemix_fig3.png)

 8. Click **Add Git** on the **Application Overview** page, which generates a Git Repository that is associated with your newly created Node.js application.
   ![Figure 4. Application Overview page](/images/bluemix_fig4.png)<br/>
   

 9. The Create Git Repository window appears. Validate that the **Populate repo with the starter app…** check box is selected so the Git Repository is populated with the starter code, and click **Continue**.
 
 10. Click **Close** when you receive the **Success!** message. You get a new GIT URL that is associated with your application. It appears under the app name and routes information.

 11. Click **Edit Code**, which opens a new browser tab and take you to the home page of the Git Repository you created.
     You are now inside {{site.data.keyword.jazzhub}}. In {{site.data.keyword.jazzhub_short}}, you can do a number of tasks that are associated with your {{site.data.keyword.Bluemix_short}} applications. These tasks include planning and tracking the development of your application, or creating stages and jobs for building and deploying your application. 
     In this example, the in-browser integrated development environment (IDE) within {{site.data.keyword.jazzhub_short}} is used to edit and deploy the Node.js application to {{site.data.keyword.Bluemix_short}}.

 12. Click `package.json` file in the left navigation window. <br/>
     You can see the contents of package.json in the right side editor window. For this example, you need an extra ssh node module dependency as part of your application. 
 
 13. Edit `package.json` to include the ssh dependency as shown in the picture. Adding `SSH2` installs the new module through NPM when your application builds.<br/>
     ![Figure 5. package.json with ssh dependency](/images/bluemix_fig5.png) 

 14. Find your `app.js` file in the left navigation menu to include more code to establish a connection to and read from your {{site.data.keyword.objectstorageshort}}. Add the code after line 19, `app.use`. The new code adds a `/slobj` route to your application that uses `SSH2` to verify connection to the storage.
    ![Figure 6. Edited code](/images/bluemix_fig6.png)
  
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
 
15. Minimize the {{site.data.keyword.jazzhub_short}} window.

## Creating {{site.data.keyword.objectstorageshort}} container on {{site.data.keyword.BluSoftlayer_notm}}

 1. Open a browser window, enter https://control.softlayer.com, and log in.

 2. Select **Storage** > **{{site.data.keyword.objectstorageshort}}**. Find your device, and click the **View Credentials** link.<br/>
    ![Figure 7. Account Credentials](/images/bluemix_fig7.png)
 
 3. Make note of your user name and API Key.
 
 4. Restore the {{site.data.keyword.jazzhub_short}} window and input your credentials (see screen capture in Step 14, lines 45, 47, and 48).
    ```
    host: '<YOUR_OBJ_STORAGE_HOST>',
    username: '<USER_NAME>',
    password: '<API_KEY>'
    ```
    
 5. Click the triangle in the {{site.data.keyword.jazzhub_short}} window to deploy your app. Click **OK** if you receive a message that prompts to stop and redeploy your application.<br/>
 ![Figure 8.](/images/bluemix_fig8.2.png)

 6. Open new browser window and enter `http://<your_bluemix_app_url>/slobj`, which activates the new route that was created in step 14 in your node.js application.
    The example code connects to the specified {{site.data.keyword.objectstorageshort}}, reads container names, and responds by rendering the container names in HTML at the route you stated.<br/>
    ![Figure 9. Page results](/images/bluemix_fig8.png)
    ![Figure 10. {{site.data.keyword.objectstorageshort}} screen within {{site.data.keyword.BluSoftlayer_notm}}](/images/bluemix_fig9.png)
