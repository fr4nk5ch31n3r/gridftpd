# gridftpd - GridFTP server configuration made easy! #

## Table of contents ##

  * [Description](#description)
  * [Prerequisites](#prerequisites)
  * [Init scripts](#init-scripts)
  * [Functionality](#functionality)
  * [Installation](#installation)
  * [License](#license)

## Description ##

Get your Globus GridFTP server up and running in less than a minute.

## Prerequisites ##

  * Globus GridFTP server binaries installed
    * Red Hat Enterprise Linux 6 and compatible: install `globus-gridftp-server-progs` package (either from the [EPEL repository] or from the [Globus repository])
    * SUSE Linux Enterprise Server 10/11: install `globus-gridftp-server-progs` package (AFAIK only available from the [Globus repository])
  * Shipped Globus GridFTP server init scripts **disabled**
(`/etc/init.d/{globus-gridftp-server|globus-gridftp-sshftp}`)
  * host certficate and key (two copies, one for the frontend and one for the
backend(s), each owned by the respective users, e.g. `globus` for the frontend and `root` for the backend(s)) available
  * trusted CA certificates available
  * `grid-mapfile` configured

[EPEL repository]: https://fedoraproject.org/wiki/EPEL
[Globus repository]: http://toolkit.globus.org/toolkit/downloads/latest-stable/

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
FQDNs, number of backends, etc.) or just accept them. No further
configuration needed for the GridFTP processes, if defaults are OK for you.

  * You can have multiple different GridFTP services on the same machine
(e.g. internal/external GridFTP services for multi-homed hosts) if you
provide a different name and FQDN for the service.

  * The number of backends is set during installation (e.g. if you want
six backends, then you just need to provide the number and the first
backend port and the installer will prepare all needed configuration files) but
can also be changed later in the init script configuration file. If you aren't
happy with the number configured during installation, stop the service,
increase or decrease the number (`GRIDFTPD_BACKENDS_NUMBER`) and restart the
service. The init script will then start as many backends as you have
configured in the init script configuration. Any backends that don't have been
configured during the initial installation step will use the default
configuration. You can adapt this by creating (a) separate configuration file(s)
for the desired backend(s).

  * By using a specific FQDN during installation (default is what
`hostname --fqdn` prints out), you can determine the network interface the
GridFTP processes should use

  * You can include backends or frontends from other hosts
(`GRIDFTPD_ADDITIONAL_BACKENDS`, `GRIDFTPD_ADDITIONAL_FRONTENDS`)

  * start/stop up to one (unprivileged) GridFTP frontend process (PI) and one or
more (privileged) GridFTP backend processes (DTPs) locally

  * per process configuration files

  * activate a specific frontend or specific backends by making its
configuration files executable or non-executable

  * list status of all activated and running GridFTP service processes locally

  * reload changed configuration files on the fly

## Installation ##

  1. Download the most current tarball from [1] or head to the releases page on
[2] and fetch a specific release

  2. Unpack to a temporary dir

  3. Enter the directory named after your target OS (e.g. SLES10, CentOS6, etc)

  4. Run the installer (preferrably as root)

  ```shell
  # ./install.sh
  ```

  5. After installation you should be able to start the GridFTP service with the
following command (assuming you used the defaults)

  ```shell
  # /etc/init.d/gridftpd start
  ```

[1]: archive/master.tar.gz
[2]: releases

## License ##

(GPLv3)

Copyright (C) 2013 Frank Scheiner  
Copyright (C) 2014, 2015 Frank Scheiner, HLRS, Universitaet Stuttgart

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

