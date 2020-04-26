# PECE N8N

This integration is the responsible for all automations on PECE project.

## Setup

### Creating password to access
1- Use this command in your terminal `echo $(htpasswd -nb user password)` where `user` and `password` are
the login in the http url access.

2- Get result terminal and put in the `N8N_HTTP_ACCESS` variable in `.env` file.

3- Start/Restart n8n docker service.

### Creating automations

#### n8n (nodemations)
Before continue it's important you know N8N
Tutorials: https://docs.n8n.io/#/tutorials

Here has many examples: https://n8n.io/workflows

#### n8n in PECE Project
![Folder Structure] (/n8n/images/folderN8N.png)

- **enabled**: Folder with the jsons files to need run.
- **base_pece_automation.json**: Base to start your automations.