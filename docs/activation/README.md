
# Activation

[[toc]]

## Getting trial license

You will need a trial activation key to be able to convert your CentOS server to CloudLinux OS Solo. The trial license subscription will work for 30 days.

To get the activation key:

1. Register with CloudLinux Network: [https://cln.cloudlinux.com/console/register/customer](https://cln.cloudlinux.com/console/register/customer) (skip it if you already registered)
2. You will receive an email with activation link
3. Login at [https://cln.cloudlinux.com/console/auth/login](https://cln.cloudlinux.com/console/auth/login)
4. Click on `Get Trial Activation Key`

You will get a key that looks like: `12314-d34463a182fede4f4d7e140f1841bcf2`

Use it to register your system or to [convert CentOS server to CloudLinux]() server.

### License activation

To register your server with CloudLinux Network using activation key run:

<div class="notranslate">

```
$ yum install rhn-setup --enablerepo=cloudlinux-base
$ /usr/sbin/rhnreg_ks --activationkey=<activation key>
```
</div>

Where activation key is like `1231-2b48feedf5b5a0e0609ae028d9275c93`

If you have IP based license, use <span class="notranslate">`clnreg_ks`</span> command:

<div class="notranslate">

```
$ yum install rhn-setup --enablerepo=cloudlinux-base
$ /usr/sbin/clnreg_ks --force
```
</div>
