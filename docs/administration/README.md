
# Administration

This section contains information that will be useful for server 
administrators that want to automatize server configuration or do some
unusual things which are not available in WEB UI.

[[toc]]

## OS Detection

To get information about current CloudLinux OS edition you can run command:

    cldetect --detect-edition
    
Response for CloudLinux OS Solo will be

    CloudLinux OS Solo 

## Best practices for virtualization templates

While we recommend and support the use of the usual [CloudLinux Solo](/installation/) installation process, 
it may require more time than is necessary for Virtual Private Server (VPS) and Virtual Machine (VM) hosts. 

Instead, you can provision VPS or VM systems with a templated environment.

### Create a minimal installation for templating

Before you begin, you need activation key that you will use for CloudLinux OS Solo installation. 
Follow the [installation](/installation/) guide and create working minimal CloudLinus OS Solo environment.
Use activation key to register your instance and get full access to repositories and run
`yum update` to fetch recent changes.

### Provisioning

We recommend using tools like `ansible` to add packages and tune server configuration.
You are free to install any Control Panels, tune settings and configure default CloudLinux tools.

### Finalize your template

If you install Control Panel in your customized template, 
please run following commands once installation is done.

    /usr/bin/package_reinstaller.py
    
Commands above will fix hooks and control panel plugins after installation.

Before you save your customized template, it is required to remove license files:

    rm -f /etc/sysconfig/rhn/jwt.token*
    rm -f /etc/sysconfig/rhn/systemid*
    rm -f /etc/sysconfig/rhn/cl-rollout*

### Updating templates

:::tip
We strongly recommend recreating templates at least once a month to keep images
fresh and up-to-date with recent CloudLinux OS Solo repositories.
:::

There are two ways of templates update:
1. Recreate them from scratch each time (recommended).
2. Boot customized template, register instance again and run `yum update`.
   Don't forget to remove license keys from template as described 
   in [Finalize your template](./#finalize-your-template).

### Next steps

Save modified environment as template and publish it for your clients.
