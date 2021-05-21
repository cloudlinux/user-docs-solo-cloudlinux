
# Licensing

[[toc]]

## Getting license

You will need a trial or payed activation key to be able to convert your server to CloudLinux OS Solo. 
Please [refer to this page](https://lp.cloudlinux.com/cloudlinux-os-solo) to find information on how to get activation key.

You will get a key that looks like: `CLSOLO-d34463a182fede4f4d7e140f1841bcf2`

Use it to register your system or to [convert CentOS server to CloudLinux]() server.

## License activation

To register your server with CloudLinux Network using activation key run:

```
yum install rhn-setup --enablerepo=cloudlinux-base
/usr/sbin/rhnreg_ks --activationkey=<activation key>
```
