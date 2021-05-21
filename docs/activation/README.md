
# Licensing

[[toc]]

## Getting license

You will need a trial or payed activation key to be able to use your CloudLinux OS Solo server. 
Please [refer to this page](https://lp.cloudlinux.com/cloudlinux-os-solo) 
to find information on how to get activation key that looks like: `CLSOLO-d34463a182fede4f4d7e140f1841bcf2`

Use it to [activate your system](./#license-activation) 
or to [convert server to CloudLinux](/installation/#converting-existing-servers) server.

:::tip Note
Activation gives you access to CloudLinux Manager features and system updates. 
:::

## License activation

To register your server with CloudLinux Network using activation key run:

```
yum install rhn-setup --enablerepo=cloudlinux-base
/usr/sbin/rhnreg_ks --activationkey=<activation key>
```
