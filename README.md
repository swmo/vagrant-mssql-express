# vagrant-mssql-express 2012

A Windows Server 2012 R2 VM with SQL Server Express 2012 R2 SP2 powered by Vagrant.
Its a fork of https://github.com/fgrehm/vagrant-mssql-express (MS SQL 2008) -> thanks to @fgrehm

## :warning: Heads up! :warning:

Same as fgrehm, its just an experiment on how to set things up for a project, I'm not planning to keep this project up to date with latest Vagrant / SQL Server updates or making additional improvements to it.

## Requirements

* Vagrant 2.0+ (tested on 2.0.1)
* VirtualBox 5.2.4 (tested on 5.2.4 )
* Around `12GB` of disk space (`3GB` for base box + `~9GB` for the VM)
tested on a macOS High Sierra 10.13.4


## Base box information

* Configured with 2 CPU and 2 GB memory by default.
* No updates or services packs applied
* The box is not activated. It has been created for testing and evaluation
  purposes only. Use of this machine for greater than 30 days will require a
  full license either via MSDN or your local Microsoft Reseller.
* The box has been created with [packer.io](http://www.packer.io/) using the
  templates made available [here](https://github.com/opentable/packer-images).

More information can be found on the [box page at Vagrant Cloud](https://app.vagrantup.com/opentable/boxes/win-2012r2-standard-amd64-nocm).

## Usage

```sh
git clone https://github.com/swmo/vagrant-mssql-express-2012.git
cd vagrant-mssql-express-2012
# Download SQL Server with Tools installer
curl http://download.microsoft.com/download/8/D/D/8DD7BDBA-CEF7-4D8E-8C16-D9F69527F909/ENU/x64/SQLEXPRWT_x64_ENU.exe --output SQLEXPRWT_x64_ENU.exe
vagrant up
# Get a coffee as it will take a while for it to finish provisioning
```

Then test the connection with the SQL Server using `telnet 192.168.10.11 1433`


### Connecting to the SQL Server instance that runs inside the VM

* IP / Host: `192.168.10.11`
* Username: `sa`
* Password: `#SAPassword!`

from unix / ubuntu you can use freetds to connect.

### Connecting to the VM using [Remote Desktop](https://en.wikipedia.org/wiki/Remote_Desktop_Protocol) connections

If you need to perform administrative tasks like importing a DB dump or creating
new databases, you can use the [`vagrant rdp` command](http://docs.vagrantup.com/v2/cli/rdp.html)
and log in with the `vagrant` user and password.

For the `vagrant rdp` command to work on Ubuntu, you'll need to `apt-get install rdesktop`
first.  On Macs, you will need [Microsoft Remote Desktop](https://itunes.apple.com/en/app/microsoft-remote-desktop/id715768417) from the Mac App Store.

## More information

If you want to know more about how the provisioning process work, check out the blog from fgrehm
[this blog post](http://helabs.com.br/blog/2014/09/19/mssql-on-vagrant/)

## Sponsor

This project was made possible thanks to [HE:labs](http://helabs.com.br/en)

## Resources

Here's some links I collected along the way while building this:
* http://www.hanselman.com/blog/DownloadSqlServerExpress.aspx
* http://msdn.microsoft.com/en-us/library/ms144259%28v=SQL.100%29.aspx
* http://technet.microsoft.com/en-us/library/ee176858.aspx
* http://iqbalnaved.wordpress.com/2013/09/28/configuration-for-connecting-to-mssql-server-2008-on-virtualbox-guestos-from-ubuntu-12-04-hostos-using-pyodbc-3-0-8/
* http://technet.microsoft.com/en-us/library/dd206997(v=sql.105).aspx
* http://sirsql.net/blog/2011/6/21/set-the-sql-tcpip-port-with-powershell.html
