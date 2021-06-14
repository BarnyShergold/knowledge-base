---
title: "Magento Cloud: reduce deployment downtime with Configuration Management"
labels: "2.1.4,2.2,2.2.x,Magento Commerce Cloud,cloud,configuration,deployment,downtime,how to,management,pipeline"
---

To dramatically reduce maintenance downtime and provide efficient configuration of your store across environments, Magento Commerce (Cloud) provides the **Configuration Management** feature. For Magento Commerce (Cloud) 2.2.x and later implementations, this feature supports Pipeline Deployment concepts and options with reduced steps.

## Overview

The painful and time-consuming issues of deploying your web store include:

* **Applying the same configuration across all environments.** Normally, you would enter configurations manually or through complicated database updates. With Configuration Management, you export configurations from the database into a single file to later push it with your code from your local development environment to Integration, Staging, and Production.
* **Site downtime when deploying static content.** Typically, static content is deployed during the [deploy phase](http://devdocs.magento.com/guides/v2.2/cloud/reference/discover-deploy.html#cloud-deploy-over-phases-hook) . This can take up to 30 minutes or more, which is not acceptable for business. Configuration Management moves static content deployment to the [build phase](http://devdocs.magento.com/guides/v2.2/cloud/reference/discover-deploy.html#cloud-deploy-over-phases-build) , which does not require downtime.

## Technology versions

* Magento Commerce (Cloud)**2.1.4** and later for Configuration Management
* Magento Commerce (Cloud)**2.2** and later for Configuration Management/Pipeline Deployment

## What is Configuration Management

To make a long story short, the Configuration Management (also known as Pipeline Deployment) process extracts all configuration settings from your Magento implementation (database) into a single PHP file. Then, you add the file to your Git commit and push it across all of your environments.

This provides the following benefits:

* **Consistent settings in all environments:** any settings being exported to the configuration file become locked (the corresponding fields in the Magento Admin become read-only), which ensures consistent configurations as you push the file across all your environments.
* **Reduced downtime:** the static file deployment shifts from the [deploy phase](http://devdocs.magento.com/guides/v2.2/cloud/reference/discover-deploy.html#cloud-deploy-over-phases-hook) (which requires the site to be in the Maintenance mode) to the [build phase](http://devdocs.magento.com/guides/v2.2/cloud/reference/discover-deploy.html#cloud-deploy-over-phases-build) (when the site is not in Maintenance mode and will not be brought down if errors or issues occur).
* **Protected sensitive data:** with Magento Commerce (Cloud) 2.2 and later, the process also exports any sensitive data (for example, payment gateway credentials) to the `env.php` file. This file should only be saved to the environment it is created in and not pushed with your Git branches.

We strongly recommend applying the Configuration Management approach in your deployment.

## Configuration Management on DevDocs

* [Configuration management for **2.1.X** ](http://devdocs.magento.com/guides/v2.1/cloud/live/sens-data-over.html) and the [example](http://devdocs.magento.com/guides/v2.1/cloud/live/sens-data-initial.html) in the *Magento Commerce (Cloud) Guide* 
* [Configuration management for **2.2.X** ](http://devdocs.magento.com/guides/v2.2/cloud/live/sens-data-over.html) and the [example](http://devdocs.magento.com/guides/v2.2/cloud/live/sens-data-initial.html) in the *Magento Commerce (Cloud) Guide* 
* [Upgrade from 2.0.X or 2.1.X](http://devdocs.magento.com/guides/v2.2/cloud/project/project-upgrade.html#old-version) section of the *Upgrade Magento Commerce (Cloud)* topic
* [Pipeline Deployment](http://devdocs.magento.com/guides/v2.2/config-guide/deployment/) in the *Magento Configuration Guide* — For Magento Commerce (Cloud), you do not need to follow the instructions in this guide. The content is strictly for reference. We already provide the build server, integration environments, and more with Cloud. ** 

