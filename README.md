# postfix-examples

Example Postfix configuration files and related content. Most often used for
reporting issues to the mailing list, but (optimistically) may also be used to
provide examples for others to follow

## repo layout

Configuration files are provided for each of the three roles that make up
a mail relay configuration. The mail relay configuration serves to collect
all mail "locally" before forwarding mail on to a central mail relay
cluster outside of our direct control.

Feedback regarding the settings is welcome as the author of this repo has
only light experience managing database servers, load-balancers and relay
servers.

### backend-relay

This role represents several "backend" Postfix servers that receive mail
from local (whitelisted) clients under our control. Valid mail is then
forwarded on to a central mail relay cluster that is managed by another team.

At present, these nodes are Ubuntu 16.04 LTS systems running Postfix 3.1.0.

### database-server

A MariaDB 10.0.x server that holds the majority of Postfix access tables, maps
and other data that is shared between all backend relay nodes. While used by
other systems for a variety of purposes, the overall usage of the box is
believed to be moderate.

### load-balancer

A HAProxy 1.7.x instance (Ubuntu PPA maintained by Debian developer) that
serves as the frontend for multiple mail relay servers. This HAProxy instance
applies regular health checks to kick failing nodes out of the backend pool.
At present, the health checks being applied represent example telnet
test connections found in various forums and guides. Feedback is welcome.
