===============
Using dnsupdate
===============

.. argparse::
   :ref: dnsupdate._get_arg_parser
   :prog: dnsupdate
   :nodefault:
   
**dnsupdate** can be run as a cron job or with any other scheduler. A systemd
service file (for use with a systemd timer) is included in the root of the
repository, but it will have to be manually installed unless you are using the
Arch Linux AUR package.

On startup, **dnsupdate** checks if the addresses for any of the configured
services have changed, and if so it will attempt to update them. If an update
fails and the service reports that the problem was due to client
misconfiguration (such as an incorrect password or hostname), the service will
be disabled until the config file is edited.

The ``-f`` flag can be used to force the update of all services, even if no
addresses have changed or a service is disabled. This flag should not be used
as part of the automatic update process because too many update attempts that
result in no change will cause some services to ban you.
