# gridftpd - GridFTP server configuration made easy! #

## Description ##

Get your Globus GridFTP server up and running in less than a minute.

## Prerequisites ##

* Globus GridFTP server binaries installed
* Shipped Globus GridFTP server init scripts disabled
(`/etc/init.d/{globus-gridftp-server|globus-gridftp-sshftp}`)
* host certficate and key (two copies, one for the frontend and one for the
backend(s)) available
* trusted CA certificates available
* `grid-mapfile` configured

## Init scripts ##

This repository provides System V init scripts for the Globus GridFTP server for
the following Linux distributions:

* Red Hat Enterprise Linux 6 (RHEL6)
* Community ENTerprise Operating System 6 (CentOS6)
* Scientific Linux 6 (SL6)
* SUSE Linux Enterprise Server 10 (SLES10)
* SUSE Linux Enterprise Server 11 (SLES11)

## Functionality ##

The following functionality is provided:

* Dialogue installer (incl. defaults) - You can change any of the
defaults (like installation dir, used certificates and keys, ports,
FQDNs, number of back ends, etc.) or just accept them. No further
configuration needed for the GridFTP processes, if defaults are OK for you.

* You can have multiple different GridFTP services on the same machine
(e.g. internal/external GridFTP services for multi-homed hosts) if you
provide a different name for the service.

* The number of back ends is set during installation (e.g. if you want
six back ends, then you just need to provide the number and the first
back end port and the installer will prepare all needed configuration files)

* By using a specific FQDN during installation (default is what
`hostname --fqdn` prints out), you can determine the interface the
GridFTP processes should bind to

* You can include back ends from other hosts (but still need to
configure those manually there. Background: The back ends are configured
so that they only accept IPC connections from the specific front end on
the same host. So the remote back ends have to accept the local front
end, too.)

## License ##

(GPLv3)

Copyright (C) 2013 Frank Scheiner

The software is distributed under the terms of the GNU General Public License

This software is free software: you can redistribute it and/or modify
it under the terms of the GNU General Public License as published by
the Free Software Foundation, either version 3 of the License, or
(at your option) any later version.

This software is distributed in the hope that it will be useful,
but WITHOUT ANY WARRANTY; without even the implied warranty of
MERCHANTABILITY or FITNESS FOR A PARTICULAR PURPOSE.  See the
GNU General Public License for more details.

You should have received a copy of the GNU General Public License
along with this program.  If not, see <http://www.gnu.org/licenses/>.

