# Introduction

[[toc]]

## What is CloudLinux OS Solo

CloudLinux OS Solo is designed for installation on VPS or dedicated servers 
with a single hosting account for any number of websites. 
Unlike [CloudLinux OS Shared](https://docs.cloudlinux.com/introduction/), 
this edition is not designed for Shared Hosting usage 
and it does not include any [LVE-related](https://docs.cloudlinux.com/lve_manager/) features.

### Benefits

We believe that this distribution will be useful for you if: 
1. as a site owner you have different performance issues with websites hosted. 
   CloudLinux OS Solo provides a set of tools for website monitoring and performance tracking out-of-box;
2. as a service provider you sell VPS servers and some of your customers require OS with extensive features 
   for better security, support, and performance.
3. as a customer you want to be sure that [product has 24/7 technical support](https://cloudlinux.zendesk.com/).

### CloudLinux OS Solo features
 
We pre-installed a couple of useful features in our distribution.

* **CloudLinux Manager**

  CloudLinux Manager is a plugin which allows you to control all the
  CloudLinux settings from an easy-to-use web UI integrated into your control panel. 
  
  The submodules you can find in CloudLinux Manager are X-Ray (PHP Slow Site Analyzer) and Website Monitoring Tool.

  [See more](/manager/).

* **Website Monitoring Tool**

  Website Monitoring Tool is a tool that allows you to track your websites uptime 
  and receive notifications about problems with access.

  Website Monitoring Tool can gather and display information regarding the slowest websites on server, 
  notify using email about errors happened on websites and send you a daily website performance reports.

  [See more](/manager/#website-monitoring-tool).

* **X-Ray**

  X-Ray or Slow Sites Analyzer is a tool developed for website performance monitoring and performance issues detection.

  X-Ray can gather and visualize information about top N slowest system functions, external requests, 
  software modules and database queries of the client’s website.

  [See more](/manager/#php-slow-site-analyzer).

### How can I try your distribution before paying for it?

We provide trial licenses for 30 days. You can get your trial key in two ways:
1. On CLN website, see [CLN registration](/cln/) section.
2. In CloudLinux Manager plugin, see [getting trial key](/manager/#activation) section.

Trial key must be entered during installation.

### CloudLinux OS Solo lifecycle

CloudLinux OS Solo has the same life cycle policy as RHEL. 
Using a supported operating system is critical to maintaining a stable server environment.

Currently, the following version are supported:

|Operating System | Release Date| End of Life and Support|
|-|--|-|
|CloudLinux OS Solo 8 | Jun 1, 2021 | May 31, 2029 |

## What's next

1. [Installation](/installation) section contains information about how to install this OS;
2. [CLN](/cln) section has instructions about how to buy license or get trial.