Steps required before starting:

Ensure Ansible 2.0 is installed (May work below, but not tested)

Create a directory to contain all Atlas related systems.

Eg.

```
mkdir -p ~/Development/Atlas/{source,server}
```

Clone this repository into the `server` folder

Run `vagrant up` and you should be good to go

The IP address of this machine is: 192.168.55.77

In your machines /etc/hosts file add the following lines:

192.168.55.77 adminer.atlas.dev
192.168.55.77 atlas.dev

To access the MySQL Database via Web

http://adminer.atlas.dev

Username: root
Password: (none)