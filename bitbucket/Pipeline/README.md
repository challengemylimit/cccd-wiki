# Setup Pipeline

## Create bitbucket-pipelines.yml

Create `bitbucket-pipelines.yml` in the root of the project.

Add rules like below

```yml
image: atlassian/default-image:latest

pipelines:
  branches:
    staging:
      - step:
          name: 'Deploy to Staging Server'
          deployment: staging
          script:
            - ssh -o StrictHostKeyChecking=no "$STG_SERVER_USER@$STG_SERVER_IP"
            - cd $STG_APP_PATH
            - git pull
            - docker-compose up -d --build
```

## Add SSH key to the repository settings

You can open `SSH Keys`

![SSH Keys Menu](https://cccd0.sharepoint.com/:i:/r/sites/ApplicationSupport/Shared%20Documents/General/Bitbucket%20docs/Pipeline/menu-ssh.png?csf=1&web=1&e=AZLOGd)

Then enter private/public keys in the sections

![SSH Keys Main](https://cccd0.sharepoint.com/:i:/r/sites/ApplicationSupport/Shared%20Documents/General/Bitbucket%20docs/Pipeline/ssh.png?csf=1&web=1&e=XXmDlB)

## Add variables to the repository settings

You can open `Repository variables`

![Variable Menu](https://cccd0.sharepoint.com/:i:/r/sites/ApplicationSupport/Shared%20Documents/General/Bitbucket%20docs/Pipeline/menu-var.png?csf=1&web=1&e=IIA54X)

Then enter private/public keys in the sections

![Variable Main](https://cccd0.sharepoint.com/:i:/r/sites/ApplicationSupport/Shared%20Documents/General/Bitbucket%20docs/Pipeline/ssh.png?csf=1&web=1&e=XXmDlB)
