---
title: Setup Private Docker Registry
intro: rapyuta.io is a platform that enables robotics solution development by providing the necessary software infrastructure and facilitating the interaction between multiple stakeholders who contribute to the solution development.
weight: 314
versions:
   free-pro-team: '*'
   enterprise-server: '*'
layout: false
permissions: rapyuta.io
showMiniToc: true
miniTocMaxHeadingLevel: 4
allowTitleToDifferFromFilename: false
mapTopic: false
hidden: false
redirect_from: []
gettingStartedLinks: []
popularLinks: []
guideLinks: []
introLinks: {}
# tags : ["deep-dives"]
slug: setup-private-docker-registry
url: /how-to-guides/account-management/setup-private-docker-registry
tags:
   - How to
---

**rapyuta.io** uses your docker pull secret during **Development>Builds** as well as **package deployment** . When you want to use a **docker image** from your private (docker) registry, you grant rapyuta.io access to your private registry by creating a docker secret.

The two types of docker pull secrets that you can create are:

* Docker Hub
* Private Registry

## Creating a docker secret

To create a docker secret for a private docker registry, do the following:

1. On the left navigation bar, click **Accounts>Secrets**.

2. Click **ADD NEW SECRET**.

3. Under **SELECT SECRET TYPE**, click **Docker secret**.

4. In the **Name** box, enter a name for the docker secret. 

{{%notice info%}}
 The name should be **less than 253 characters**, **contain a-z 0-9 and hyphen**,  and **must begin and end with a-z**.
{{%/notice%}}
 
5. You can select the executable type as one of the following.
   * Dockerhub
   * Private Registry

6. If your executable type is [**Docker Hub**](https://hub.docker.com/), do the following.

   a. Type your user name, password, and Email ID in the respective fields.

7. If your executable type is a private registry, do the following in the respective fields.

   a. **Private registry**: Provide the private (docker) registry URL.

   b. **Registry Url** box: It is mandatory to provide the registry URL.

   c. In the **Username** box: Type in your docker username.

   d. In the **Email** box: Enter the valid email address associated with your docker registry.

8. Click **SUBMIT**. The docker secret for the rapyuta.io platform is created.

## Authorization Token

When you create a docker pull secret for a private registry, rapyuta.io stores your docker credentials (that is, username and password) in base64-encoded format. This encoded data is the *_ authorization token_* which gives access to rapyuta.io to pull private docker images while deploying a package.

To determine your docker credentials for a private registry, run the following instructions in sequence on the system you have logged in to docker:

1. Docker login process creates or updates **`config.json`** file. To display this file, run the  following command:

```bash
cat ~/.docker/config.json
```
???    A sample **`config.json`** file will look like:

   ```json
   {
       "auths":{
          "https://index.docker.io/v1/":{
             "auth":"c3r...ze2"
          }
       }
    }
   ```

The value of **`auth`** entry is base64-encoded data called *_ authorization token_*. If you use a docker credentials store, you will instead see `credsStore` entry with the name of the store as value. For example, a sample `config.json` file with `credsStore` entry would look like:

   ```bash
   {
       "auths":{
           "https://index.docker.io/v1/":{}
       },
       "credsStore": "osxkeychain"
   }
   ```

   You can find out the authorization token from the respective  `credsStore` entry???s value. In this case, use `osxkeychain` value to figure out the authorization token.

2. To convert *_ authorization token_* to a readable format, execute the command:

   ```bash

   echo  "c3r...ze2" | base64  -d

   ```

3. The output consists of two parts separated by a colon **:** as shown below

   ```bash

   janedoe:xxxxxxxxxx

   ```

   The part to the left of **:** is your docker username, while the one on the right is your password.

 If you encounter the following deployment error, Ensure the docker username and password in a secret are correct.

  ```bash
  DEP_E153 (Could not pull either the docker image or the built package artifact for the component on the cloud)
  ```

## Related Links

* [About Secrets](/1_understanding-rio/12_core-concepts/#secrets)