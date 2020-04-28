# PECE N8N

This integration is the responsible for all automations on PECE project.

## Setup

### .env variables
- **N8N_CLIENT_ID**: Consumer UUID to use with OAuth 2.0 and get API.
- **N8N_CLIENT_SECRET**: Client secret in consumer.
- **SITE_N8N_USERNAME**: Username to create n8n user in PECE project.
- **SITE_N8N_PASSWORD**: Password to create n8n user in PECE project.
- **N8N_HTTP_ACCESS**: User and password to authenticate in n8n url.

Below has the explanation about each variable

#### SITE_N8N_USERNAME and SITE_N8N_PASSWORD
If you set this variables before install PECE project then you don't need continue this step, 
only if you change user and password from n8n

1- Define password to n8n user in the PECE Project.
![Folder Structure](images/n8n-define-password.gif)
If you wish you can also change the n8n name too.

2- Add new username and password in the `SITE_N8N_USERNAME` and `SITE_N8N_PASSWORD`.

#### N8N_CLIENT_ID
After install PECE project, you need get the consumer UUID and put in this variable

1- Access `Configuration > Web Service > Consumer`

2- Copy UUID from n8n consumer or other consumer.

![Put N8N_CLIENT_ID](images/get-n8n-client-id.gif)

#### N8N_CLIENT_SECRET
You need create the client secret in the consumer

1- Write client secret in .env

2- Copy and paste client secret in the consumer

![Put N8N_CLIENT_ID](images/n8n-client-secret.gif)


#### N8N_HTTP_ACCESS
1- Use this command in your terminal `echo $(htpasswd -nb user password)` where `user` and `password` are
the login in the http url access.

2- Get the result on terminal and paste in the `N8N_HTTP_ACCESS` variable in `.env` file.

3- Start/Restart n8n docker service.

Example with user `test` and password `test`
```shell
$ echo $(htpasswd -nb test test)
test:$apr1$5/03Eb6p$5Zk5OB.xI.j0HBlT69heb.
```

### Automations

#### n8n (nodemations)
Before continue it's important you know N8N
Tutorials: https://docs.n8n.io/#/tutorials

Here has many examples: https://n8n.io/workflows

#### n8n in PECE Project

##### Folder structure
![Folder Structure](images/folder-n8n.png)

- **enabled**: Folder with the jsons files to need run.
- **base_pece_automation.json**: Base to start your automations.

##### Creating workflow
1- Import the json base file
![Import the json](images/import-n8n-json.gif)

- **PECE Essay Created**: Webhook example to call when new PECE Essay is Created
- **Get Authentication Token**: Call the python script using the .env variables to create OAuth 2.0 token.
- **GraphQL**: Call PECE API to get more information

You can access each node for see the settings.

2- Complete your workflow with others nodes.

3- Save your workflow and enable.

![Save and Enable workflow](images/save-enable-workflow.gif)

4- Create the rule event in the PECE project to call your workflow, for default the `save_pece_essay` is intalled.

1.  Access `Configuration > Workflow > Rules > Edit save_pece_essay`
2.  Edit Action `Webhook Post`
3.  Update the URL to your webhook URL.
![Rule Edit](images/rule-edit.gif)

4.  Update `API User Name` and `API User Password` to your user and password if you added Authentication property in the Webhook node in n8n.
5.  Save your rule.

5- Test your workflow.
1.  To test you need change your Webhook URL in the rule to test url, step 4

![URL Test](images/url-test.png)

2.  Click in the `Execute Workflow`

3.  Now, register a PECE Essay

![Test n8n](images/test-n8n.gif)


Look the result in RocketChat:

![Result in RocketChat](images/rocketchat.png)


6- Download your workflow and add in the `n8n-automation/enabled`. Don't forget change the url test to url prod in PECE Project on production.
![Download Workflow](images/download-workflow.gif)

##### Enable automations
Run `make start-automations` after install PECE project or update/create workflows