```bash
sudo passwd <user> #password change in console
su <user> #substitute user
#Fedora18 menu editor
sudo yum install -y alacarte
/etc/sudoers format
username host=(user:group) tag:commands
gy ALL=(ALL:ALL) NOPASSWD:/path/to/command or ALL

#dynaTrace install.sh
sudo rm -R /opt/dynatrace-6.1.0
```
#### java
```
java -version #java executed by default; useful: http://ice.he.net/~hedden/jrelinux.html
locate 'bin/java' lists all java* files in bin dirs; /usr/lib/java dirs empty on Fedora 16, /usr/lib/jvm seems to contain originally used Java version
#As only /usr/bin is in the $PATH this seems to be the root for Java symlink chain
which java returns /usr/bin/java which seems to be the root of the symlink chain
rpm -q jre returns jre-1.7.0_05-fcs.i586 on Fedora 16; file is in /usr/java
file /usr/bin/java returns /usr/bin/java: symbolic link to '/etc/alternatives/java'
#On Fedora 16 /usr/bin/java symlinks to /etc/alternatives/java and that to /usr/lib/jvm/jre-1.6.0-openjdk/bin/java
#SymLink from /usr/bin/java (/usr/bin is in PATH) to wanted java version executable in Fedora 16
sudo ln -s /usr/java/jdk1.7.0/jre/bin/java /usr/bin/java
#Solaris or AIX installations w/o private Java get a -vm argument written into dtserver.ini or dtcollector.ini!
```
```
#### auto-start init.d daemon
sudo rm /etc/init.d/dynaTraceServer
#make link to script
sudo ln -s /opt/dynatrace-5.6.0/init.d/dynaTraceServer /etc/init.d/dynaTraceServer
#### register daemon
sudo chkconfig --add dynaTraceServer
#Ubuntu 14.04 interactive; 14.04 using upstart, not systemd
sudo sysv-rc-conf
#Debian Ubuntu - old dynaTrace 3.5 outdated example. argument dynaTrace instead of dynaTraceServer
sudo update-rc.d dynaTraceServer defaults
#Ubuntu uncheck not enough to update-rc.d with defaults. must
sudo update-rc.d dynaTraceServer remove
#but my 14.10 runlevel = 2, so defaults (3 and 5) don´t work!!!
#to get rid of sudo sysv-rc-conf entries w/o start on any runlevel
#delete .sh and -P cache after sudo update-rc.d dynaTraceServer remove:
sudo sysv-rc-conf -P
```
#### Linux commands, other:
```bash
#change Ubuntu env DEFAULT_RUNLEVEL=2 to 5
sudo nohup gedit & /etc/init/rc-sysinit.conf
sudo /usr/bin/nautilus #Ubuntu filer
sudo su #root console
echo $0 #returns used shell
cd - go home / ~
pwd = present / current working directory = cwd
mv "old location" "new location" = move and rename files and dirs, e.g. rename java symlink: cd /usr/bin, sudo mv java javaOld
/etc/init.d is symlink to rc.d/init.d and the latter contains init.d and rc[0-6].d
uname -r linux kernel version
dmesg #bootloader messages
```
#### nautilus #filer #explorer
```
#context menu option util
sudo apt install xdotool nautilus-actions
```
#### bash
```bash
bash#!/bin/sh
#i in string = interactive shell
echo $-
```
```
#dynaTrace unattended install silent install Linux
#fedora16-32vm
cd /opt !!!!!!!!!!!!!!!!!
echo "Y" | sudo java -jar /mnt/hgfs/D/Prg/dynaTrace/dynatrace-5.6.0.5802-linux-x86.jar
#sudo chmod -R 755 dynatrace-6.2.0 # owner group everybody #4 read, 2 write, 1 execute
#chmod +x prgname
echo "Y" | sudo java -jar /mnt/hgfs/D/Prg/dynaTrace/dynatrace-easytravel-2.0.0.1245-linux-x86.jar
#fedora18-64
cd /opt !!!
#5.6 2013 Fall
#### HD
echo "Y" | sudo java -jar /run/media/gy/Gate/Prg/dynaTrace/dynatrace-6.1.0.7877-linux-x64.jar
sudo java -jar /run/media/gy/Gate/Prg/dynaTrace/dynatrace-easytravel-2.0.0.1245-linux-x86_64.jar
#6.0 2014 Spring
#### HD ##Fedora 18
sudo rm -R /opt/dynatrace-6.2
cd /opt
echo "Y" | sudo java -jar /run/media/gy/Gate/Prg/dynaTrace/dynatrace-6.1.0.7880-linux-x64.jar
echo "Y" | sudo java -jar /run/media/gy/Gate/Prg/dynaTrace/dynatrace-6.2.0.1239-linux-x64.jar
sudo java -jar /run/media/gy/Gate/Prg/dynaTrace/dynatrace-easytravel-2.0.0.1245-linux-x86_64.jar
sudo chown -R gy:gy /opt/dynatrace-6.0.0
sudo rm -R /opt/dynatrace-6.1.0
cd /opt
echo "Y" | sudo java -jar /run/media/gy/Gate/Prg/dynaTrace/dynatrace-6.1.0.7880-linux-x64.jar
sudo java -jar /run/media/gy/Gate/Prg/dynaTrace/dynatrace-easytravel-2.0.0.1566-linux-x86_64.jar
sudo chown -R gy:gy /opt/dynatrace-6.1.0
#### MICRON32
echo "Y" | sudo java -jar /run/media/gy/MICRON32/Prg/dynaTrace/dynatrace-5.6.0.5802-linux-x64.jar
sudo java -jar /run/media/gy/MICRON32/Prg/dynaTrace/dynatrace-client-5.6.0.5802-linux-x86.jar
sudo java -jar /run/media/gy/MICRON32/Prg/dynaTrace/dynatrace-easytravel-2.0.0.1245-linux-x86_64.jar
#sudo chmod -R 755 easytravel-2.0.0
#### Downloads
echo "Y" | sudo java -jar ~/Downloads/dynatrace-6.1.0.7880-linux-x64.jar
#VM name Ubuntu1410 host name osboxes
sudo rm -R /opt/dynatrace-6.2
smb://TAG00944648039/f/Prg/Dynatrace first.last pw
cd /opt
echo "Y" | sudo java -jar ~/Downloads/dynatrace-6.2.0.1239-linux-x64.jar
sudo tar -xzf ~/Downloads/dynatrace-nodejsagent-6.2.0.1239-linux-x64.tgz
sudo chown -R gy:gy /opt/dynatrace-6.2
-Dcom.dynatrace.diagnostics.startDtangAdapter=true
#kill -15 <pid>

sudo rm -R /opt/dynatrace-6.3
smb://TAG00944648039/f/Prg/Dynatrace
cd /opt
echo "Y" | sudo java -jar ~/Downloads/dynatrace-6.3.0.1305-linux-x64.jar
sudo tar -xzf ~/Downloads/dynatrace-nodejsagent-6.3.3.1020-linux-x64.tgz
sudo java -jar ~/Downloads/dynatrace-6.3.0.1305-darwin-x86.jar
sudo chown -R gy:gy /opt/dynatrace-6.3
sudo chown -R guenter.huber:Admin /opt/dynatrace-6.3

sudo java -jar ~/Downloads/dynatrace-easytravel-2.0.0.1788-linux-x86_64.jar
sudo chown -R gy:gy /opt/easytravel-2.0.0-x64
sudo rm -R /opt/easytravel-2.0.0-x64

settings > dynaTrace Server services email:
mailhost-at.emea.cpwr.corp 25 non-SSL no username / pw; admin mail guenter.huber@dynatrace.com
smtp.live.com? port or smtp-mail.outlook.com 25!?, 465?, 587!? SSL? TLS! guenter_huber22@hotmail.com pw
smtp.gmail.com 465 = SSL username guenter.huber22@gmail.com pw
smtp.mail.yahoo.com 587 non-SSL username guenter.huber@yahoo.com pw

#### process status
#list processes with user they started under, PID, CPU, mem,...
ps -auxf
#check if server is running
ps ax | grep dtserver
#or shorter
ps -A | grep dtserver

#### dynaTrace Server on Linux 32 bit instrumentation: add to dtserver.ini as last line
-agentpath:/opt/dynatrace-5.6.0/agent/lib/libdtagent.so=name=dTServer_Monitoring,server=lnz124597n02
#### dynaTrace Collector on Linux instrumentation: add to dtcollector.ini as last line
-agentpath:/opt/dynatrace-5.6.0/agent/lib/libdtagent.so=name=dTCollector_Monitoring,server=lnz124597n02
#don´t forget Agent Group(s?) and Agent mappings

#### Host Agent: Host-Agent-only on Linux for lnz124597n02
#change Server in /opt/dynatrace-5.6.0/agent/conf/dthostagent.ini
#don´t forget to map host in some Agent Group
sudo /opt/dynatrace-5.6.0/agent/lib/dthostagent

#### CICS zRemote Agent on Fedora18-64 (-bg doesn´t, & works sort of)
nohup /opt/dynatrace-5.6.0/agent/lib64/dtzagent zdclistenerport=8898 name=CICS_Monitoring server=fedora18-64 &

#### dynaTrace instrumentation
JAVA_OPTS=$JAVA_OPTS -agentpath:/opt/dynatrace-5.6.0/agent/lib/libdtagent.so=name=dynaTrace_Monitoring,server=lnz124597n02:9998

#start local Client and easyTravel to install System Profile
or
easyTravel System Profile installation other than localhost
Client > Settings > dynaTrace Servers > Plugins > Install Plugin <eT_Home>/easyTravel-plugin.dtp

#dtserver rights after install: -rwxr--r--
#files in virgin server/conf after install: keystore.jks
#files in server/conf after first start: baselining.hidden.properties, cmdb.config.xml, ipmappings.xml, mqmappings.xml, server.config.xml, user.permissions.xml, userproperties.xml
#### after a while: statuscenter.xml

#unattended install Windows
msiexec /passive /i dynatrace-agent-5.0.0.3924.msi ADDLOCAL="DiagnosticsAgent,DotNetAgent,DotNetAgent20x64,HostAgent,HostAgentx64" /liemo InstallLog.txt

proxy setup in SuSE: Configure Desktop Network Settings > set AutoProxy; extra for YAST in YAST > Proxy
proxy setup in Fedora: manual proy in network settings
or
~/.bash_profile:
export http_proxy=http://cns-lnz.emea.cpwr.corp:8001
export https_proxy=http://cns-lnz.emea.cpwr.corp:8001
export ftp_proxy=http://cns-lnz.emea.cpwr.corp:8001
and
sudo gedit /etc/yum.conf in [main] section
proxy=http://cns-lnz.emea.cpwr.corp:8001
proxy_username=
proxy_password=
and
for wget
sudo gedit /etc/wgetrc
uses environment
#firewall in Fedora used to be:
/etc/init.d/iptables save
/etc/init.d/iptables stop
#permanent
chkconfig iptables off

#firewall in Fedora 16:
sudo -i
system-config-firewall
#firewall in Fedora 18 replaced iptables in favor of firewalld.
sudo yum remove firewalld

#firewall in Fedora 18:
firewall-config

#https://community.compuwareapm.com/community/display/DOCDT56/Server+Configuration#ServerConfiguration-NumberofOpenFiles/FileDescriptorsLimiton*NIX
#### file handles
#nr of files currently in use
more /proc/sys/fs/file-nr
#returns on Fedorea 16: 5248	0	411376
#### "maximum number of open file descriptors" - Soft limit on fedora 16-32
ulimit -n
#returns 1024
#set limit to 2048
ulimit -n 2048
#hard limit
ulimit -Hn

####  check for original value (411376 on Fedora 16, sample says nonsense 8196) with:
cat /proc/sys/fs/file-max
#write bigger number into file-max:
echo 512000 > /proc/sys/fs/file-max
#to set values for users: /etc/security/limits.conf - sehr fraglich! use ulimit!
@gy soft nofile 2048
*=everybody
#trashed the whole system with value 3096 in sysctl.conf before I knew above command!!!
sudo gedit /etc/sysctl.conf
#add / change and force update
fs.file-max =
sudo sysctl -p

For VMware:
sudo yum update kernel
sudo yum install gcc make binutils
sudo yum install kernel-headers kernel-devel

#fedora (18) Software Update
sudo yum update --skip-broken

#### VMware Tools after unzip into Downloads with Archive Man:
cd Downloads/vmware-tools-distrib
sudo ./vmware-install.pl

#/usr/bin/vmware-toolbox-cmd #never used

#### edit selinux
/etc/selinux/config
SELINUX=disabled

32 bit Webstart Client on 64 bit Linux
JLT-66955 32-bit versions of gtk and jvm needed to run client under linux
SUSE122-64 GTK installed; I installed swt and libXtst-32; ???(g)libc
#Fedora 18 working command (errors see below):
sudo yum install libcanberra-gtk2.i686 gtk2-engines.i686
PackageKit-gtk-module.i686 not found
Manual install of libpk-gtk-module.so found at
http://rpmfind.net/linux/rpm2html/search.php?query=libpk-gtk-module.so
(search for Fedora 16) doesn´t help!
#errors:
Gtk-WARNING **: Unable to locate theme engine in module_path: "adwaita"
Gtk-Message: Failed to load module "pk-gtk-module"
/usr/lib/gtk-2.0/modules/libpk-gtk-module.so missing
#alternative grapevine
sudo yum install gtk-murrine-engine gtk-murrine-engine.i686
sudo yum install -y gtk2-engines gtk2-engines.i686 libcanberra-gtk2 libcanberra-gtk3 libcanberra-gtk2.i686 libcanberra-gtk3.i686
sudo yum install gtk3-engines gtk3-engines.i686 libcanberra-gtk3 libcanberra-gtk2.i686 libcanberra-gtk3.i686

sudo -i
#symbolic link
sudo ln -s [TARGET DIRECTORY OR FILE] ./[SHORTCUT in different dir]
#points a symbolic link "./logs" to "/usr/local/apache/logs" (from different dir!!!)
sudo ln -s /usr/local/apache/logs ./logs

#chkconfig updates  and queries runlevel information for system services on e.g. Fedora (16)
#update-rc.d on Debian Ubuntu
#sudo sysv-rc-conf interactive on Ubuntu
chkconfig --list [<name>]
sudo chkconfig --add <name>
sudo chkconfig --del <name>

#/etc/rc.conf and /etc/rc.local not in Fedora (16) OOTB
#fedora 16 gfedora16vm old http://172.16.98.13 new http://172.16.100.87
#fedora 18 fedora18-64 http://172.16.102.6
#Hyper-V name SuseHV121 = GS121HV.site 10.0.0.6

#### Hyper-V dis/enable as admin (on?)
bcdedit /set hypervisorlaunchtype off
bcdedit /set hypervisorlaunchtype auto
#### VMware Player not compatible w Device/Credential Guard; INTIMIDATING solution w bsedit:
https://kb.vmware.com/s/article/2146361
#on Windows 10 gpedit.msc (similarity to regedt32.exe?)
#NOT Windows Server gpmc.msc (Group Policy Management Console)
Computer Configuration > Administrative Templates > System > Device Guard > Turn on Virtualization Based Security
#REASONABLE solution?: PowerShell as admin and .\inFrontOfCmd like in Linux
cd C:\Users\gy\Downloads\DeviceGuardCredentialGTool
.\DG_Readiness_Tool_v3.2.ps1 -Ready

#Hyper-V Checkpoints (use Production NOT Std ones for real consistency!!) - uses Volume Shadow Copy Service or File System Freeze on a Linux virtual machine

#### Hyper-V state in PowerShell Get-VM... https://technet.microsoft.com/de-de/library/hh848479.aspx
Get-Command -Module hyper-v | Out-GridView
#Linux Integration Service installed? (already on Red Hat and similar)
Get-VMIntegrationService
Get-VMFirmware

#### Hyper-V w Ubuntu 16.04 on Windows 1709
#set HV dirs
#add external network card to connect wifi
sudo nohup gedit /etc/default/grub
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash video=hyperv_fb:1920x1080"
sudo update-grub
#restart and change sth in Display settings and back (e.g. Sticky edges) to avoid error
#network drives with Nautilus: Connect to Server; smb://g10; hotmail address, domain hotmail.com, pw
#no clipboard integration with Ubuntu and VNC; guess would need RDP on Ubuntu for VMConnect or Remote Desktop

#link with same name points to dynaTraceServer start / stop / restart shell script
#link practical example
cd /etc/init.d
sudo ln -s /opt/dynatrace-5.5.0/init.d/dynaTraceServer ./
#chkconfig practical example
sudo chkconfig --add dynaTraceServer

#Add Tier php 32 bit Web Server Agent - add WS Agent if no other dynaTrace installation
cd /opt
sudo ./dynatrace-wsagent-5.5.0.5226-linux-x86.sh

#fedora:
sudo gedit /opt/dynatrace-5.6.0/agent/conf/dtwsagent.ini
#SuSE
kdesu /usr/bin/kwrite /opt/dynatrace-5.6.0/agent/conf/dtwsagent.ini
#change Agent name to be a bit more unique
Name dtwsagentApache

#add to opt/lampp/etc/httpd.conf (last LoadModule)
LoadModule dtagent_module "/opt/dynatrace-6.2/agent/lib/libdtagent.so"

#add to opt/lampp/etc/php.ini (bottom)
extension=/opt/dynatrace-6.2/agent/lib/libdtagent.so

#### Start PHP scenario
#s start dT Server
cd /opt/dynatrace-6.1.0
./dtserver
#start master Agent as it is no longer started by the slave as of 6.0
cd /opt/dynatrace-6.1.0/init.d
sudo ./dynaTraceWebServerAgent start
#p start #apache #lampp, #php and #mySQL
cd /opt/lampp
sudo ./lampp startapache
sudo ./lampp startmysql

#### start PHP w/o Web server
#start master Agent
cd /opt/dynatrace-5.5.0/init.d
sudo ./dynaTraceWebServerAgent start

#### start PostgreSQL on Fedora 16
cd /opt/PostgreSQL/9.1
bin/postgres -D data
#start pgAdmin III
opt/PostgreSQL/9.1/scripts/launchpgadmin.sh
#PostgreSQL login from dynaTrace 5.6 on Fedora 16
User: postgres Password PosNNxxxx Host: localhost Port: 5432

#nohup - run cmd in & in background w/o stopping it by logout
#start filer on Fedora & Ubuntu
sudo nohup nautilus &
#start filer on SuSE

#ipconfig == ifconfig in Linux (at least Fedora)

Remote Desktop for root
File /etc/rc.config
ROOT_LOGIN_REMOTE=yes

On SUSE (KDE) use F5 Shell @ boot screen to boot into console, in Ubuntu
sudo /etc/init.d/gdm stop
or
/sbin/init 3
or
^alt backspace (twice)
to kill GUI and then ^alt F1 for console - in Fedora ^alt F1 for Gnome, ^alt F2 for console!!!

shutdown now
reboot
reboot -f

/usr/bin/nvidia-settings

release notes /usr/local/cuda/doc

PATH
/usr/local/cuda/bin

export PATH=$PATH:/usr/local/cuda/bin

permanent in
~/.bash_profile
but as it doesn´t exist in
~/.bashrc
#modified by root (gy)
export PATH=$PATH:/usr/local/cuda/bin
export LD_LIBRARY_PATH=$LD_LIBRARY_PATH:/usr/local/cuda/lib64:/usr/local/cuda/lib
#export SDK_INSTALL_PATH=$SDK_INSTALL_PATH:/usr/local/cuda/sdk
export SDK_INSTALL_PATH=$SDK_INSTALL_PATH:~/NVIDIA_GPU_Computing_SDK

LD_LIBRARY_PATH
for 64-bit
/usr/local/cuda/lib64:/usr/local/cuda/lib

export LD_LIBRARY_PATH=$LD_LIBRARY_PATH:/usr/local/cuda/lib64:/usr/local/cuda/lib

or add to /etc/ld.so.conf
for 64-bit
/usr/local/cuda/lib64
/usr/local/cuda/lib

and run ldconfig as root

export SDK_INSTALL_PATH=$SDK_INSTALL_PATH:/usr/local/cuda/sdk

gcc --version

sudo apt-get install freeglut3-dev build-essential libx11-dev libxmu-dev libxi-dev libgl1-mesa-glx libglu1-mesa libglu1-mesa-dev

#### apt
sudo apt update
sudo apt upgrade
sudo apt autoremove
#fix missing packages
sudo apt -f install
#or
sudo apt-get update
sudo apt-get upgrade
sudo apt-get autoremove
sudo apt-get -f install

yum dasselbe wie apt-get, aber andere Paketnamen
Fedora 14:
freeglut 2-3 packets
build-essential ?
libx11-dev installed?
libxmu-dev runtime installed, changed to / added dev pack
libxi-dev same
libgl1-mesa = Mesa libGL ok
libglu1-mesa = Mesa libGLU
libglu1-mesa-dev contained in other Mesa?

nVidia Control Panel
/usr/bin/nvidia-settings

result:
/usr/local/cuda/sdk/C/bin/linux/release/

JRE x as default
http://www.64bitjungle.com/ubuntu/install-java-jre-160-update-x-on-hardy-as-the-default-java-runtime/
chmod 755 /opt/java/32/jre-6u16-linux-i586.bin
chmod 755 /opt/java/64/jre-6u16-linux-x64.bin
cd /opt/java/64
./jre-6u16-linux-x64.bin
update-alternatives --install "/usr/bin/java" "java" "/opt/java/64/jre1.6.0_16/bin/java" 1
update-alternatives --set java /opt/java/64/jre1.6.0_16/bin/java

Eclipse Galileo SW Addition (CDT e.g.) @ GT
http://download.eclipse.org/releases/galileo
The Eclipse Project Updates
http://download.eclipse.org/eclipse/updates/3.6

Eclipse Helios SW Addition (CDT e.g.) @ GL
http://download.eclipse.org/releases/helios
The Eclipse Project Updates
http://download.eclipse.org/eclipse/updates/3.6

Eclipse Kepler 4.3
WTK WebToolKit WTP WebToolsPlatform for Samsung TV 2014 IDE-SDK-5.1
UE40HU6900 Unique ID P7CL6GDVZ4NNE FW-Version T-NT14UDEUC-1060.4
UE55HU7580
http://download.eclipse.org/webtools/repository/kepler/
Google Pepper 31 Portable NAtiveCLient SDK PNaCl (needs python 2.7.x)
https://developer.chrome.com/native-client/sdk/download
#unzip to devtools
y:
cd Y:\workspaces\devtools\nacl_sdk
naclsdk list
naclsdk update
#Set environment variable (only 1, other 2 are PATHs; Y: for co-PC!) for Samsung Eclipse integration
NACL_SDK_ROOT F:\workspaces\devtools\nacl_sdk\pepper_44
#PATH, NOT environment variable!
PEPPER_TOOLS_PATH F:\workspaces\devtools\nacl_sdk\pepper_44\tools
PEPPER_TOOLCHAIN_PATH F:\workspaces\devtools\nacl_sdk\pepper_44\toolchain\win_pnacl\bin
#home-PC: activate Google Chrome NaCl in chrome://flags/ doesn´t help; naclrocks in Chrome Web Store helps! Removed PATH !envi var! for C:\Users\gy\AppData\Roaming\npm (Node Package Manager)

#### Eclipse
https://dev-wiki.emea.cpwr.corp/display/DEV/dynaTrace+-+Getting+Started+-+Development+and+Build+Environment

Eclipse CUDA Add
http://ydl.net/eclipse_cuda_plugin/helios/

edit sudoers as su:
su
sudo gedit /etc/sudoers
add line:
gy ALL=(ALL) ALL

Change owner -Recursively to gy:gy (user:group) for folder /opt and files??? chown dT!
#NO! not good for Apache?: chown -R gy:gy /opt
sudo chown -R gy:gy /opt/dynatrace-6.0.0

http://proxyconf.emea.cpwr.corp/

#dynaTrace install asks for target dir
java -jar ~/Downloads/dynatrace-4.2.0.3154-linux-x86.jar

#XAMPP #LAMPP 1.8.1 Apache 2.4.3 PHP 5.4.7
#install 32 bit
tar xvfz xampp-linux-1.8.1.tar.gz -C /opt
#install 64 bit from Downloads to /opt
sudo ./xampp-linux-x64-1.8.2-0-installer.run
#problems with tar.gz
chown -R root:nogroup "/opt/lampp/apache2/htdocs"
chown -R nobody:nogroup /opt/lampp/logs
#solution on fedora 18, now tar.gz installed!
yum install libstdc++.i686 zlib.i686

#unpack Agent: cd /opt first because .sh doesn´t ask!
cd /opt
./dynatrace-wsagent-5.5.0.5226-linux-x86.sh
#Instrument:
#fedora:
sudo gedit /opt/lampp/etc/httpd.conf
#SuSE
kdesu /usr/bin/kwrite /opt/lampp/etc/httpd.conf
#EOF:
LoadModule dtagent_module <path>/libdtagent.so

#xampp #lampp #mysql #phpmyadmin enable by
sudo gedit /opt/lampp/etc/extra/httpd-xampp.conf
add Require all granted
<Directory "/opt/lampp/phpmyadmin">
    AllowOverride AuthConfig Limit
    Order allow,deny
    Allow from all
    Require all granted
</Directory>

#xampp
http://localhost/security/xamppsecurity.php
set mySQL root pw none on G10 #? rooNNxxx
XAMPP DIRECTORY PROTECTION (.htaccess)
XAMPP lampp directory is protected now! All personal data was safed in the following file:
C:\xampp\security\xampp.users
C:\xampp\htdocs\xampp\.htaccess

#### wordpress on lampp
create wordpress DB in mySQL
if files were copied from wordpress.zip wordpress folder into /opt/lampp/htdocs/blog
localhost/blog/ should create wp-config.php if permissions are right, but had to do it manually
dynaBlog user gy mail cw

#### PrestaShop on lamp
create prestashop db in mySQL; unzip and
cd /opt/lampp/htdocs
sudo mv /home/gy/prestashop prestashop
chmod -R 777 prestashop
#should be dir / files 775 / 664 afterward installation (configuration), but didn´t work here - blank browser pages

#.bash_profile or .bashrc
export DT_HOME=/opt/dynatrace-5.5.0

#Java Control Panel for Java path in Fedora in Apps > Other Java
#Fedora 16-32 after Oracle JDK 1.7 RPM install w/o jre/bin portion
export JAVA_HOME=/usr/java/jdk1.7.0

#### datastax apache cassandra on fedora 16 (32bit) / all Linux
java -version should be 6!
cd ~/Downloads
curl -OL http://downloads.datastax.com/community/dsc.tar.gz
cd /opt
sudo tar -xvzf ~/Downloads/dsc.tar.gz
sudo mkdir /var/lib/cassandra
sudo mkdir /var/log/cassandra
sudo chown -R  $USER: $GROUP /var/lib/cassandra
sudo chown -R  $USER: $GROUP /var/log/cassandra

#datastax apache cassandra JVM_OPTS instead of JAVA_OPTS!!!
#/opt/dsc-cassandra-1.2.5/conf/cassandra-env.sh
add
-agentpath:"/opt/dynatrace-5.5.0/agent/lib/libdtagent.so"=name=CassandraAPMNG,server=lnz124597n02:9998
to
JVM_OPTS="$JVM_OPTS -ea"
leave out quotes from -agentpath; becomes
JVM_OPTS="$JVM_OPTS -agentpath:/opt/dynatrace-5.5.0/agent/lib/libdtagent.so=name=CassandraAPMNG,server=lnz124597n02:9998 -ea"

#datastax cassandra opsCenter
python -V
openssl version
iostat -V
cd ~/Downloads
curl -OL http://downloads.datastax.com/community/opscenter.tar.gz
cd /opt
sudo tar -xzvf ~/Downloads/opscenter.tar.gz
#Set the [webserver] interface in conf/opscenterd.conf - not necessary for localhost / 127.0.0.1:8888

#cassandra start: DO NOT cd into bin
cd /opt/dsc-cassandra-1.2.5
#as cassandra is installed for the current user sudo ./cassandra is nonsense
./cassandra
#cassandra datastax opsCenter start:
cd /opt/opscenter-3.1.1
bin/opscenter

#### APMng on WindowsVM instrumentation with Classic on Windows in
add
 -agentpath:"C:\Program Files (x86)\dynaTrace\dynaTrace 5.5.0\agent\lib64\dtagent.dll"=name=APMNG,server=lnz124597n02:9998
to C:\CompuwareAPM-1.0\startServer.bat resulting in
../jre/bin/java -agentpath:"C:\Program Files (x86)\dynaTrace\dynaTrace 5.5.0\agent\lib64\dtagent.dll"=name=APMNG,server=lnz124597n02:9998 ...
or on Linux (should actually be in /opt instead of ~/)
add
 -agentpath:"/opt/dynatrace-5.5.0/agent/lib/libdtagent.so"=name=APMNG,server=lnz124597n02:9998
to /home/gy/CompuwareAPM-1.0/startServer.sh resulting in
../jre/bin/java -agentpath:"/opt/dynatrace-5.5.0/agent/lib/libdtagent.so"=name=APMNG,server=lnz124597n02:9998 ...

#APMng start on WindowsVM
cd \CompuwareAPM-1.0
startServer
#on Linux
cd /home/gy/CompuwareAPM-1.0
./startServer.sh

#### Oracle WebLogic
cd /opt/WebLogic
chmod 755 configure.sh
./configure.sh

#Setup WebLogic environment in the current shell.
$MW_HOME/wlserver/server/bin/setWLSEnv.sh

#after Oracle WebLogic install
export MW_HOME=/opt/WebLogic
chmod 755 config.sh
#start GUI
cd $MW_HOME/wlserver/common/bin
./config.sh

#WebLogic Fedora16-32 mydomain webNNxxx AdminServer 7001
#MangedServer1 7003 SSL 7503 UnixMachine1 5556 AdminServer connected to UnixMachine1
#folders mydomain and domain_base admin=weblogic pass=webNNxxx
/opt/WebLogic/mydomain/base_domain
#folder domain2 admin=weblogic2 pass=webNNxxx
/opt/WebLogic/domain2/base_domain w/o managed server and EnterpriseDB
http://gfedora16vm:7001

#WebLogic GCW82-64 Win8 CTP instrumentation
set JAVA_OPTIONS=-agentpath:"C:\Program Files (x86)\dynaTrace\dynaTrace 4.2.0\agent\lib\dtagent.dll"=name=WebLogic,server=GHUBER:9998 %JAVA_OPTIONS%
@REM gcw8:9998 gcw8:10098 localhost:10098 GHUBER:9998 GHUBER2:10098

#config.sh instance GUI
/home/gy/Oracle/WebLogic/common/bin
./config.sh
#node manager configuration (to use startWebLogic.sh)
ORACLE_COMMON_HOME/common/bin/setNMProps.sh
#node manager - configure first!
/home/gy/Oracle/WebLogic/server/bin
startNodeManager.sh

#### samba smb on fedora 18
sudo gedit /etc/selinux/config
SELINUX=disabled
sudo gedit /etc/samba/smb.conf
#from smb.conf
sudo setsebool -P samba_domain_controller on
sudo setsebool -P samba_enable_home_dirs on
workgroup = ARBEITSGRUPPE
server string = Samba Server Version %v
;	interfaces = lo eth0 192.168.12.2/24 192.168.13.2/24
#added 10.0.0. for home network
hosts allow = 10.0.0. 127. 192.168.12. 192.168.13.
security = user
#
passdb backend = tdbsam
#
systemctl enable smb.service
systemctl start smb.service
#result for Fedora 18 on LNZ machine:
smb://TAG00944648039/F/Prg/Dynatrace
smb://TAG00944648039/part2/Prg
smb://TAG00944648039/F/Prg/Dynatrace
mount -t smbfs //TAG00944648039/f/ /mnt/TAG00944648039/f/ -o username=gy

#Ubuntu - first share on a new Windows machine!!!:
smb://172.16.101.236 user DYNATRACE/guenter.huber domain DYNATRACE

#### /etc/sudoers explanation
username ALL=NOPASSWD:/path/to/command
username ALL=(ALL) NOPASSWD:/path/to/command
username ALL=(ALL:ALL) NOPASSWD:/path/to/command

username host=(user:group) tag:commands

host specifies the host names this line is valid for. Unless you are sharing asudoers file among different hosts that need different rules using the special value ALL meaning "all hosts" is a good choice.

user specifies which users you can use with the -u options to run the command. If you omit this you can't use the -u option.

group specifies which groups you can use with the -g options. If you omit it you can't use the -g option.

Both user and group understand the special value ALL as "all users/groups"

If you omit the whole (user:group) thing you can't use -u and -g but only run the command as root.

tag lets you specify some options, like NOPASSWD: ALL

With example 1 you can run the command as root but can't use -u and -g to run it as any other user or group.

With example 2 you can run the command as root or use -u to run it as any other user.

With 3 you can run the command as root or use -u or -g to run the command as any other user or group.

#### Updates
yum list updates
yum list installed
rpm -qa | grep httpd*
yum list extras
yum whatprovides /etc/passwd

#### Ubuntu 14.10 host name osboxes when bridged (not NAT) 172.16.110.50
user osboxes.org pw osboxes.org
#### Ubuntu1604
sudo apt update
sudo apt upgrade
sudo apt autoremove
#list groups or install Users and Groups, cuz the normal Users control doesn´t show groups
cat /etc/group
#Open VMware #OpenVMware Tools install on converted #AudiCar #Virtualbox #Ubuntu 16.04
sudo apt install open-vm-tools open-vm-tools-desktop

#boot repair
sudo add-apt-repository ppa:yannubuntu/boot-repair
sudo apt-get update
sudo apt-get install -y boot-repair && boot-repair

#remove openJDK
sudo apt-get purge openjdk-\*
sudo mkdir -p /usr/local/java
cd /usr/local/java
sudo tar xvzf ~/Downloads/jdk-8u77-linux-x64.tar.gz
sudo gedit /etc/profile
#add to profile
JAVA_HOME=/usr/local/java/jdk1.8.0_77
JRE_HOME=$JAVA_HOME/JRE
PATH=$PATH:$HOME/bin:$JAVA_HOME/bin
export JAVA_HOME
export PATH
#tell the system that the new Oracle Java version is available for use: JRE, JDK, webstart
sudo update-alternatives --install "/usr/bin/java" "java" "/usr/local/java/jdk1.8.0_77/bin/java" 1
sudo update-alternatives --install "/usr/bin/javac" "javac" "/usr/local/java/jdk1.8.0_77/bin/javac" 1
sudo update-alternatives --install "/usr/bin/javaws" "javaws" "/usr/local/java/jdk1.8.0_77/bin/javaws" 1
#Java JDK/JRE must be the default Java
sudo update-alternatives --set java /usr/local/java/jdk1.8.0_77/bin/java
sudo update-alternatives --set javac /usr/local/java/jdk1.8.0_77/bin/javac
sudo update-alternatives --set javaws /usr/local/java/jdk1.8.0_77/bin/javaws

#### Windows Subsystem for Linux installed in C:\Users\gy\AppData\Local\lxss
#### bash on Ubuntu on Windows https://msdn.microsoft.com/commandline/wsl/about
#Windows drives mounted under /mnt


#### nginx config location
#sudo -i to change to root
sudo gedit /etc/nginx/nginx.conf
#htdocs inetpub equivalent
/usr/share/nginx/html
#fedora
yum install nginx-full-dbg ?
#ubuntu
sudo apt-get update
sudo apt-get install nginx-full-dbg
#chkconfig --add nginx
sudo apt-get install sysv-rc-conf
sudo sysv-rc-conf
#misc
sudo service nginx restart
sudo update-rc.d nginx defaults
sudo LD_PRELOAD=/opt/dynatrace6.2.0/agent/lib64/libdtagent.so nginx

#### node.js Ubuntu
sudo apt-get install node.js
sudo apt-get install node
sudo tar -xzf ~/Downloads/dynatrace-nodejsagent-6.2.2.1019-linux-x64.tgz
sudo chown -R gy:gy /opt/dynatrace-6.2
try { require('/opt/dynatrace-6.2/agent/nodejs/nodejsagent.js')({ server: 'http://osboxes:8040', agentName: 'Node.js_Monitoring' }); } catch (err) { console.error(err.toString()); }
strace bin/node js/serverHello.js 2>&1|grep node

#### node.js Windows installed 0.12.4
#### Cordova HTML CSS JavaScript apps
npm install -g cordova
#Cordova in
C:\Users\cwat-ghuber\AppData\Roaming\npm\cordova
#??? -> C:\Users\cwat-ghuber\AppData\Roaming\npm\node_modules\cordova\bin\cordova
cd C:\Users\cwat-ghuber\Cordova
C:\Users\cwat-ghuber\AppData\Roaming\npm\cordova create MyApp
cd MyApp
#C:\Users\cwat-ghuber\AppData\Roaming\npm\cordova platform
#Available platforms: amazon-fireos, android, blackberry10, firefoxos, webos, windows, windows8, wp8
C:\Users\cwat-ghuber\AppData\Roaming\npm\cordova platform add browser
#Creating Browser project. Path: platforms\browser
#Discovered plugin "cordova-plugin-whitelist" in config.xml. Installing to the project
C:\Users\cwat-ghuber\AppData\Roaming\npm\cordova run browser


#### Android
#### notification panel Benachrichtigungen to switch to Media Transfer Protocol more easily than w Settings > Developer >

#### Android app bar ActionBar http://developer.android.com/training/appbar/index.html vs. ToolBar in Android support lib w backward compat

#### Firefox remote debugging on Android
about:config
#find devtools.debugger.remote-enabled
#or Settings > Dev tools
#description for host
https://developer.mozilla.org/en-US/docs/Tools/Remote_Debugging/Firefox_for_Android
#WebView debugging
if (Build.VERSION.SDK_INT >= Build.VERSION_CODES.KITKAT) {
  WebView.setWebContentsDebuggingEnabled(true);
}

#### Android Studio install: unzip to ~
cd android-studio/bin
./studio.sh

#### Android Studio 64bit Windows
#### Gradle use default gradle wrapper - nogo -> local Gradle distri
#gradlew getHomeDir
C:/Users/cwat-ghuber/.gradle/wrapper/dists/gradle-2.4-all/3i2gobhdl0fm2tosnn15g540i0/gradle-2.4
#cd C:\Users\cwat-ghuber\AndroidStudioProjects\ATest3
#gradlew build


#### VMware change boot order,... in .vmx file to force BIOS or delay boot 10 sec for F2 into BIOS
bios.forceSetupOnce = "TRUE"
bios.bootDelay = "10000"

####  Windows 8.3 8dot3 filenames disabled by default on 8.1
fsutil 8dot3name query c:

#### Samsung Galaxy Tab2 3300c0cb4b816275
#### SideSync interfering with ADB?
#### Samsung USB driver for mobile phones?
C:\workspaces\sdks\android\platform-tools\adb
LogCat in Android Studio?

#### maps.google.com ##Wallern longitude 13.95 latitude 48.2333 h 978 ft 298 m

#### Samsung Galaxy Tab S2 files in Samsung Link
storage/emulated/0/files
#SD-card named storage/extSdCard

#### Wear Android Wear
#app maintainance: Einstellungen > Apps & Benachrichtigungen


#### TightVNC leave full screen ^-alt-shift-f or ^esc
#Search Your Computer for Desktop Sharing to configure Vino
#### Ubuntu enable #VNC w/o encryption; gconf-editor built-in (Configuration Editor):
#TightVNC: no matching security type
sudo apt-get install dconf-tools
#Ubuntu 16.04 software > search dconf > install
#search for require-encryption (is in org->gnome->desktop->remote-access)
ps ax | grep vino #just in case: check if vino #vnc-server is running


#### gparted partitioning
sudo apt-get install gparted
#### fdisk linux e.g. to fix sector size:
sudo fdisk /dev/sdb
#m help, d delete partition, n new partition, p list part, w!!! write part table and quit


#### Mac ###Macintosh
smb://quickbuild.emea.cpwr.corp/dist guenter.huber@dynatrace.org pw
#//emea.cpwr.corp/at mounted under /Volumes/at/home/lnz/cwat-ghuber
smb://emea.cpwr.corp/at/home/lnz/cwat-ghuber guenter.huber@dynatrace.org pw
\\172.16.99.168
\\Klauss-MacBook-Air.local local???
smb://klauss-air.clients.emea.cpwr.corp ???
smb://klauss-air.clients.dynatrace.org ???
#### Xcode Mac installed for all /just current user
cd "/Library/Application Support/Developer/Shared/Xcode/Plug-ins"
cd "~/Library/Application Support/Developer/Shared/Xcode/Plug-ins"
#to open the current directory from terminal in Finder:
open .
#show hidden files on Mac
defaults write com.apple.finder AppleShowAllFiles YES
killall Finder
#Homebrew brew.sh packet manager
brew install wget
brew install nmap
#check for PORT (like ping for ip)
nmap -p 8021 192.168.99.100

#### Java locations on Mac
#Runtime automatically updated:
Library/Internet Plug-ins/...
#JDKs installed from Oracle d/l, default dir:
/Library/Java/JavaVirtualMachines/jdk1.7.0_60.jdk/Contents/Home/jre/bin/java
/Library/Java/JavaVirtualMachines/jdk1.8.0_71.jdk/Contents/Home/jre/bin/java

#### Dynatrace
sudo rm -R /opt/dynatrace-6.3
cd /opt
sudo java -jar ~/Downloads/dynatrace-6.3.0.1278-darwin-x86.jar
sudo chown -R guenter.huber:guenter.huber /opt/dynatrace-6.3


#### Watch Apple Watch
#app force-quit: long-press side-button (shutdown,...) long-press crown


#### Docker on Ubuntu
**************
#### Ubuntu 16.04: https://docs.docker.com/engine/installation/linux/ubuntulinux/
#### optional: https://docs.docker.com/engine/admin/systemd/#custom-docker-daemon-options
#start docker with systemd as boot and service manager
sudo systemctl start docker
#daemon / service at boot:
sudo systemctl enable docker
#/etc/init.d/docker #/etc/init/docker.conf #/etc/rc5.d
#/etc/default/docker #not for systemd; everything commented out
systemctl show docker | grep EnvironmentFile #returns nothing
systemctl show --property=FragmentPath docker #returns
FragmentPath=/lib/systemd/system/docker.service
#empty ExecStart= defeats autostart
sudo nohup gedit /lib/systemd/system/docker.service


sudo apt-get upgrade docker-engine
sudo apt-get purge docker-engine
sudo apt-get autoremove
rm -rf /var/lib/docker
****************
#### docker commands:
docker info
#Commit your container (diff to orig) to a new named image
docker commit <container> <some_name>
#assign running container to environment variable
JOB=$(docker run -d ubuntu /bin/sh -c "while true; do echo Hello; sleep 1; done")
#apply var to stop, restart, kill, rm container
docker start $JOB
#list all containers, not only running
docker ps -a
#stop all running containers
docker kill $(docker ps -q)
#delete all containers
docker rm $(docker ps -a -q)
docker images
#delete all images
docker rmi $(docker images -q)
#delete image force
docker rmi -f <numericImageIDOr(2ndPartOf)Name>
#Delete all untagged / dangling images
sudo docker rmi $(docker images -q -f dangling=true)


#### Docker github on Ubuntu GQ
#github Bernd Atlassian sourcetree
#description on https://github.com/Dynatrace/Dynatrace-Docker
#extra terminal window for netcat key server
cd Downloads
nc -l 1337 < dtlicense.key
#clones into ~/Dynatrace-Docker
cd
git clone https://github.com/Dynatrace/Dynatrace-Docker.git
cd Dynatrace-Docker
DT_SERVER_LICENSE_KEY_FILE_URL=http://$127.0.0.1:1337 docker-compose up

#### Docker experiments with http://jdlm.info/articles/2016/03/06/lessons-building-node-app-docker.html
#problems if npm version not specified
#put Dockerfile and docker-compose.yml in ~/Node-Docker/chat and
docker-compose up #to create image and start container to echo ready and exit
#run interactive shell in a container created from the image:
docker-compose run --rm chat /bin/bash #results in app@e1613d86a8e5:~/chat$
#and use it to set up the initial package files:
npm init --yes
npm shrinkwrap
#exit container shell
exit
#install tree command referenced in sample
sudo apt-get install tree


#### Docker native apps on Win and Mac
#### need not find out Docker IP; always docker on Win & docker.local on Mac

#### Docker Dynatrace
docker pull dynatrace/server
eval "$(docker-machine env default)" #to config Mac (bash) shell
sudo nc -l 80 < ~/Downloads/dtlicense.key
./DtDockerServer.sh
DT_SERVER_LICENSE_KEY_FILE_URL=http://172.16.100.21 docker-compose up
#Safari dtserver Services 8020
192.168.99.100:32771
docker stop dtserver

#### Docker on Mac:
#### Terminal / bash:
#nginx webserver on 8000:
docker run -d -p 8000:80 nginx
#### VirtualBox Oracle virtualizer Docker window:
#docker root /mnt/sda1/var/lib/docker
JOB=$(docker run -d ubuntu /bin/sh -c "while true; do echo Hello; sleep 1; done")
docker start $JOB #stop, restart, kill, rm


#### github
#### create repository username.github.io on github using brwoser: gue22.github.io
#to clone the repo, in the git cmd window enter:
cd \xampp\htdocs
git clone https://github.com/gue22/gue22.github.io
#or
git clone https://github.com/ai-bits/ai-bits.github.io.git
#create gue22.github.io/index.html
cd gue22.github.io
#or edit README.md so html is created via Jekyll
https://github.com/ai-bits/ai-bits.github.io/edit/master/README.md
#or edit locally and (on Ubuntu)
cd ai-bits.github.io/
git add *
#to set your account's default identity
git config --global user.email "guenter.huber22@gmail.com"
git config --global user.name "ai-bits"
git commit README.md -m "car kits part 1"
git push -u origin master

#### online-bookmarks #xampp #php C:\xampp\htdocs\online-bookmarks
#after install.php renamed to installRenamedToHideIt.php
#admin pw admin changed to admNNxxx; gy tinNNxxx
#mysql bookmarks backup see http://www.frech.ch/online-bookmarks/installation.php
cd C:\xampp\mysql
mkdir backup\bookmarks #for first backup
C:\xampp\mysql\bin\mysqldump --user=root --password bookmarks > backup\bookmarks\bookmarks-bak.sql

#### draft-js JavaScript rich text editor framework, built for React
cd \xampp\htdocs
git clone https://github.com/facebook/draft-js.git
cd draft-js
npm install
npm run build


#### tinyMCE forked
git clone https://github.com/gue22/tinymce.git
cd \xampp\htdocs
#install grunt command line tool globally
npm i -g grunt-cli
#install all package dependencies
npm i
#build TinyMCE by writing
grunt


#### ruxit doc stack - files from Ingo in f:/Prg/ruxit
#for jekyll: install ruby (here 2.2.4 32 bit) and ruby dev kit DevKit-mingw64-32 into c:/RubyDevKit
cd /ruby22
ruby dk.rb init
ruby dk.rb install #bind ruby to devKit
#gems are in C:\Ruby22\lib\ruby\gems\2.2.0\gems
#jekyll Windows was installed as a ruby gem by Ingo with
gem install jekyll
#resulting in 3.1.2; suggestion: gem uninstall jekyll -v 3.1.2; gem install jekyll -v 2.5.1
#Jekyll config is in C:\Ruby22\lib\ruby\gems\2.2.0\gems\jekyll-3.1.2\lib\site_template\_config.yml
#recommendation: frequently run
cd /ruby22
gem update && gem cleanup
#install gulp into project directory (as admin???)
cd C:\xampp\htdocs\Dynatrace-New-Doc-Example\node_modules
npm install gulp
#global install gulp (after local!); npm rm --global gulp #if already installed globally
npm install gulp -g
#gulp needs all dependencies installed to create the needed styles, scripts and images folders
npm install --saveDev
#create styles: source _sass folder and sub-folders and css folder (main css)
gulp styles


#### Dynatrace newdoc
cd c:\xampp\htdocs
git clone https://github.com/Dynatrace/Dynatrace-New-Doc-Example
#install all prerequisites to the doc dir
https://community.dynatrace.com/community/pages/viewpage.action?title=Ruxit+Doc+Stack+Installation&spaceKey=DOCDT99
jekyll serve --incremental


#### git server Ubuntu #Fedora
sudo apt-get install git #sudo yum install git
#config
git config --global user.email "guenter_huber22@hotmail.com"
git config --global user.name "gy"
cd /opt
sudo mkdir git
cd git
sudo mkdir newdoc
cd ..
sudo chown -R gy:gy /opt/
#create repository
git init /opt/git/newdoc
#
cd
mkdir git
cd git
#ignore "empty repo" warning:
git clone gy@osboxes:/opt/git/newdoc #git clone gy@fedora18-64:/opt/git/newdoc
#edit some files
cd newdoc
#Commit all local changes with message (otherwise VIM! -> exit VIM with esc :x or :wq)
git commit -a -m 'index.html'
git push origin master # Push changes to the server's version of the repository
#sync repo and clone
git pull #git fetch + git merge; compare git push


#### Sublime Text
#Settings User
{
	"ignored_packages":
	[
		"Vintage"
	],
	"tab_size": 2,
	"translate_tabs_to_spaces": true
}
#View menu > Show Console > paste py for Package Control from https://packagecontrol.io/installation
#shift^P > Install Package > markdown; Git;

#### Udacity Machine Learning Intro using python 2 and not python3
python -V
#numpy and scipy don´t seem to be installed on Ubuntu 16.04, so import fails
sudo apt install python-numpy
sudo apt install python-scipy
sudo apt install python-matplotlib
pip -V
sudo apt install python-pip
#update pip dubious variants
pip install --upgrade pip #upgrades to ~; not done on G10 bash
#suggested in gym
pip install --ignore-installed pip
#when using pip from the Ubuntu distro the following two packages work:
pip install scikit-learn
pip install nltk
sudo apt install git
#better not install to pwd (with period at the command end) but to ud120-projects
git clone https://github.com/udacity/ud120-projects.git

#### CUDA
#### CUDA 8.0 Debian package
sudo dpkg --install cuda-repo-ubuntu1604-8-0-local-ga2_8.0.61-1_amd64.deb
sudo apt-get update
sudo apt-get install cuda

#### CUDA 9.1 Debian package
https://docs.nvidia.com/cuda/cuda-installation-guide-linux/index.html #ubuntu-installation
sudo dpkg -i Downloads/cuda-repo-ubuntu1604-9-1-local_9.1.85-1_amd64.deb
#sudo apt-key add /var/cuda-repo-<version>/7fa2af80.pub #translates to:
sudo apt-key add /var/cuda-repo-9-1-local/7fa2af80.pub
#sudo apt-key adv --fetch-keys https://developer.download.nvidia.com/compute/cuda/repos/<distro>/<architecture>/7fa2af80.pub #translates to (actual protocol is httpS!!!)
sudo apt-key adv --fetch-keys http://developer.download.nvidia.com/compute/cuda/repos/ubuntu1604/x86_64/7fa2af80.pub
sudo apt update
sudo apt install cuda
#### version management
sudo apt autoremove #removed CUDA 8
#### version management alternative
sudo apt install synaptic
#### to (completely) remove: Synaptic Package Manager > Installed (local or obsolete)
#### to (completely) remove in console:
sudo apt-get remove --purge nvidia*
sudo apt-get autoremove
sudo reboot
#set env vars in ~/.bashrc? (not in Nvidia, but TensorFlow doc!)
export LD_LIBRARY_PATH="$LD_LIBRARY_PATH:/usr/local/cuda/lib64:/usr/local/cuda/extras/CUPTI/lib64"
export CUDA_HOME=/usr/local/cuda
#according to Nvidia CUDA docs
export PATH=/usr/local/cuda-8.0/bin${PATH:+:${PATH}}


#### TensorFlow
#check TensorFlow version tf version:
python -c 'import tensorflow as tf; print(tf.__version__)'
#installed for Python 2 and working on g7 in 2017

#### TensorFlow GPU on G10 Windows 10
#### Anaconda3 5.0.1 in c:\dl\Anaconda3 for user gy only
#### installer added to PATH and registered as default Python 3.6
#open Anaconda prompt
#Create a conda environment called tensorflow w explicit TF python version:
conda create -n tensorflow python=3.6
#creates env in C:\dl\Anaconda3\envs\tensorflow
activate tensorflow #source activate tensorflow #in bash
#### TF install doc content title: Pip installation ON WINDOWS
#tensorFlow 1.5 GPU!! new install needs CUDA 9.0! cuDNN64_6
pip install --ignore-installed --upgrade tensorflow-gpu
#TensorFlow ends up in c:\dl\anaconda3\envs\tensorflow\lib\site-packages
#install Jupyter notebook (and libs) for TensorFlow env (with TF activated!)
conda install jupyter
#### additional installs for Magnus Peterson´s Tensorflow-Tutorials
conda install matplotlib #installs numpy, intel-openmp, mkl
conda install scipy #installs numpy too
conda install scikit-learn
pip install keras #as conda wants dependency TF 1.1.0!
#python versions, depending on env set
pip list

#### TensorFlow on Ubuntu/Linux 64-bit VM Ubuntu1604 on g10, CPU AVX2, Python 3.6.0 Anaconda 4.3.0
#install
cd Downloads
bash Anaconda3-4.3.0-Linux-x86_64.sh
conda create -n tensorflow python=3.6
#to work and keep up-to-date:
source activate tensorflow
#### TensorFlow AVX2 20171113
pip install --ignore-installed --upgrade https://github.com/mind/wheels/releases/download/tf1.4-cpu/tensorflow-1.4.0-cp36-cp36m-linux_x86_64.whl

#set TensorFlow env vars in ~/.bashrc necessary?
export LD_LIBRARY_PATH="$LD_LIBRARY_PATH:/usr/local/cuda/lib64:/usr/local/cuda/extras/CUPTI/lib64"
export CUDA_HOME=/usr/local/cuda

#### TensorFlow on Ubuntu 16.04 128GB USB standalone for Dell
#### download and install Anaconda 4.2.0 64 bit Python 3.5
https://www.continuum.io/downloads
bash Downloads/Anaconda3-4.2.0-Linux-x86_64.sh
#install location ~/Anaconda3 prepended to PATH in /home/gy/.bashrc
#Create a conda environment called tensorflow w specific python -V
conda create -n tensorflow python=3.5
source activate tensorflow
#to deactivate tensorflow:
#source deactivate
#### install dependencies for https://github.com/mind/wheels/releases/tag/tf1.4.1-gpu-cuda91
#install MKL (lengthy compile!)
#sudo apt install cmake #probably installed
git clone https://github.com/01org/mkl-dnn.git
cd mkl-dnn/scripts && ./prepare_mkl.sh && cd ..
mkdir -p build && cd build && cmake .. && make
sudo make install
echo 'export LD_LIBRARY_PATH=$LD_LIBRARY_PATH:/usr/local/lib' >> ~/.bashrc
#install MPI
sudo apt-get install mpich
#contrary to doc: pip, not pip3 install!
#actually used Download:
pip install --ignore-installed --upgrade https://github.com/mind/wheels/releases/download/tf1.4.1-gpu-cuda91/tensorflow-1.4.1-cp35-cp35m-linux_x86_64.whl

conda install jupyter
jupyter notebook --no-browser
localhost:8888 #beware to use the token stated when jupyter notebook server is started!
#TensorFlow directory
python -c 'import os; import inspect; import tensorflow; print(os.path.dirname(inspect.getfile(tensorflow)))'
#returns /home/gy/anaconda3/envs/tensorflow/lib/python3.5/site-packages/tensorflow

#### TensorFlow AVX2 on 64GB USB for NUC GNUB Ubuntu 16.04
#https://github.com/mind/wheels
conda create -n tensorflow python=3.6
#20180103
pip install --ignore-installed --upgrade https://github.com/mind/wheels/releases/download/tf1.4.1-cpu/tensorflow-1.4.1-cp36-cp36m-linux_x86_64.whl

#### TensorFlow Docker install on 128GB USB - 3 GB download
docker run -it -p 8888:8888 gcr.io/tensorflow/tensorflow:latest-devel-gpu

#### TensorFlow Docker removal:
#list containers incl running (-a)
docker ps -a
docker rm <gid>
docker images
docker rmi <gid>


#### TensorFlow Learn tf-learn image recognition https://github.com/Marsan-Ma/imgrec
#train model and inference work w the below
#### tflearn.org ##TensorFlow Learn installed on G10 to run \dl\tf\imgrec for MNIST 17flowers
cd tf
git clone https://github.com/Marsan-Ma/imgrec.git
activate tensorflow
#prerequisites for tflearn
conda install h5py
#curses Windows (Ubuntu not necessary) d/l https://www.lfd.uci.edu/~gohlke/pythonlibs/#curses
pip install curses-2.2-cp35-none-win_amd64.whl
#conda install tflearn #doesn´t work, so:
pip install tflearn
#pwd \dl\tf\imgrec
mkdir images
cd images
mkdir 17flowers
cd ..
#DO NOT d/l Dataset images from http://www.robots.ox.ac.uk/~vgg/data/flowers/17/ BUT
python dump_17flowers.py #d/l and separate samples into folders C:\dl\tf\imgrec\images\17flowers\jpg\0 to 16 according to label
#17flowers training
python train.py --model_name 17flowers --label_size 17 #c:\tmp\tflearn_logs

#### predict 17flowers using Flask server
#prerequisites for Flask: NOT yaml but PYyaml! GNUC Ubuntu anaconda 5.0.1 -> custom
conda install pyyaml, requests, flask
cd ~/tf/imgrec #cd \dl\tf\imgrec
python app.py --model_name 17flowers --label_size 17
localhost:8883
#URL e.g.
https://www.theflowerexpert.com/media/images/mostpopularflowers/morepopularflowers/daffodil/daffodil1.jpg
#### Python webserver to serve images used in model (because file:// not working with Flask)
cd ~/tf/imgrec/images/17flowers/jpg/0 #cd \dl\tf\imgrec\images\17flowers\jpg\0
python -m http.server 8882
#serve sample image:
http://localhost:8882/image_0001.jpg
#file:// formats tested with Flask that didn´t work:
#file:///c:/dl/tf/imgrec/images/17flowers/jpg/0/image_0001.jpg
#file:///home/gy/dl/tf/imgrec/images/17flowers/jpg/0/image_0001.jpg
#file:///localhost/home/gy/dl/tf/imgrec/images/17flowers/jpg/0/image_0001.jpg
#file://images/17flowers/jpg/0/image_0001.jpg

#### TensorFlow models
cd ~/tf
git clone https://github.com/tensorflow/models.git
#https://github.com/tensorflow/models/blob/master/object_detection/g3doc/installation.md
#Windows
conda install pillow
conda install lxml
#Ubuntu (pil = Python Image Lib = pillow)
sudo apt-get install protobuf-compiler python-pil python-lxml
#from tf/models/
protoc object_detection/protos/*.proto --python_out=.
export PYTHONPATH=$PYTHONPATH:'pwd':'pwd'/slim
cd ~/tf/models/object_detection

#### model for classifying handwritten digits from the MNIST dataset
cd /home/gy/anaconda3/envs/tensorflow/lib/python3.5/site-packages/tensorflow/models/image
#creates a $pwd/data subdir and starts the model
python -m tensorflow.models.image.mnist.convolutional

#### TensorFlow Slim ##tf-slim ##tfslim in tf/models git clone
https://github.com/tensorflow/models/tree/master/research/slim/
#tf-slim old in inception sub-tree of older models0 folder structure; current v in:
cd ~/tf/models/research/slim #g10: cd C:\dl\tf\models\research\slim
DATA_DIR=/mnt/hgfs/F/data/17flowers
python download_and_convert_data.py --dataset_name=flowers --dataset_dir="${DATA_DIR}"

#tensorflow optimization #universal approximator
#both terminals:
source activate tensorflow
cd C:\dl\tf\approxUniversal
#terminal 1:
python uat3.py --nb_neurons 50
#terminal 2:
tensorboard --logdir results --reload_interval 5

#tensorflow mnist_tutorial
#both terminals:
source activate tensorflow
cd ~/tf/mnist_tutorial
#terminal 1:
python mnist_tutorial.py
#terminal 2:
tensorboard --logdir log

#### Hvass-labs ~/tf/TensorFlow-Tutorials/01_Simple_Linear_Model
#01_Simple_Linear_Model_annotated for libs needed,...

#### Atari 2600 VCS emulator Stella
https://stella-emu.github.io/downloads.html
sudo dpkg -i Downloads/stella_5.0.2-1_amd64.deb
sudo apt update
stella

#### Atari Pong prerequisites
#### gym openAI install
cd
git clone https://github.com/openai/gym.git
#unzipped repo from 2016 in gym1 (gynONE!)
#cd gym
#pip install -e .[all] #all requires cmake and pip
#pip install 'gym[all]' on new Ubuntu1604gym still required
sudo apt install python-numpy python-dev cmake zlib1g-dev libjpeg-dev xvfb libav-tools xorg-dev python-opengl libboost-all-dev libsdl2-dev swig
#didn´t install gym python modules from git clone (like above), but with
pip install 'gym[all]' #into tensorflow env
#gym1/pg-pong.py: import cPickle as pickle #applies to python 2; instead use
import pickle #for python 3

#### universe openAI install
source activate tensorflow
git clone https://github.com/openai/universe.git
cd universe
pip install -e .
#Docker install
sudo apt update
#Install packages to allow apt to use a repository over HTTPS:
sudo apt-get install apt-transport-https ca-certificates curl software-properties-common
#Add Docker’s official GPG key:
curl -fsSL https://download.docker.com/linux/ubuntu/gpg | sudo apt-key add -
#Docker stable
sudo add-apt-repository "deb [arch=amd64] https://download.docker.com/linux/ubuntu $(lsb_release -cs) stable"
sudo apt-get update
sudo apt-get install docker-ce
#Docker specific version:
#sudo apt-get install docker-ce=<VERSION>
#Docker as non-root user
sudo usermod -aG docker gy
#universe build
docker build -t universe .
#Docker pytest
docker run --privileged --rm -e DOCKER_NET_HOST=172.17.0.1 -v /var/run/docker.sock:/var/run/docker.sock universe pytest

#### TensorFlow Tutorials Hvass Laboratories
git clone https://github.com/Hvass-Labs/TensorFlow-Tutorials.git
source activate tensorflow
#### additional prerequisites to TF, gym
conda install matplotlib
pip install prettytensor
#### reinforcement learning TensorFlow Tutorial #16
jupyter notebook --no-browser
TensorFlow-Tutorials/16_Reinforcement_Learning.ipynb
#train MsPacman
cd tf/TensorFlow-Tutorials
python reinforcement_learning.py --env 'MsPacman-v4' --training
#play MsPacman
python reinforcement_learning.py --env 'MsPacman-v4' --render --episodes 20
#after an hour ca 1050 max; after ca 24 hours:
Rewards for 20 episodes:
- Min:    330.0
- Mean:   812.0
- Max:    2330.0
- Stdev:  452.709619955
Rewards for 20 episodes:
- Min:    670.0
- Mean:   1431.5
- Max:    2010.0
- Stdev:  353.995409575

#### TensorFlow www.oreilly.com/ideas/reinforcement-learning-for-complex-goals-using-tensorflow
#### https://github.com/awjuliani/dfp
[source] activate tensorflow
#prerequisite imageio - at least for Win64:
conda install --channel https://conda.anaconda.org/conda-forge imageio

#### keras Francois Chollet
source activate tensorflow
#Keras 2.1.1
pip install keras
#Keras reinforcement learning Keras downgraded to 2.0.6
pip install keras-rl

#### TensorFlow git repo on gu1604 128 GB USB
cd #to clone to ~/tensorflow
git clone https://github.com/tensorflow/tensorflow

#https://bazel.build/versions/master/docs/install.html
#Add Bazel distribution URI as a package source (one time setup)
echo "deb [arch=amd64] http://storage.googleapis.com/bazel-apt stable jdk1.8" | sudo tee /etc/apt/sources.list.d/bazel.list
curl https://bazel.build/bazel-release.pub.gpg | sudo apt-key add -
sudo apt-get update && sudo apt-get install bazel
#needed or updated with Ubuntu anyway?
sudo apt-get upgrade bazel

#Getting bash completion for bazel
bazel build //scripts:bazel-complete.bash #fails with
#the 'build' command is only supported from within a workspace

sudo apt-get install libcupti-dev

#build TensorFlow with GPU support
bazel build -c opt --config=cuda //tensorflow/tools/pip_package:build_pip_package
#toDo
mkdir _python_build
cd _python_build
ln -s ../bazel-bin/tensorflow/tools/pip_package/build_pip_package.runfiles/org_tensorflow/* .
ln -s ../tensorflow/tools/pip_package/* .
python setup.py develop

#### TensorFlow git clone for compilation
cd
git clone https://github.com/tensorflow/tensorflow

#### bazel Google build environment and Java on Ubuntu
#OpenJDK
sudo apt-get install default-jre
sudo apt-get install default-jdk
#Oracle Java
https://wiki.ubuntuusers.de/Java/Installation/Oracle_Java/Java_8/
#manage Java default for multiple installations. also for javac, javadoc and jarsigner
sudo update-alternatives --config java
#pwd == ~
git clone https://github.com/bazelbuild/bazel.git
cd basel
./compile.sh #? ./compile.sh compile output/bazel
#copy exe to a directory on the PATH
cd /usr/local/bin
sudo cp /home/gy/bazel/output/bazel .

#### TensorFlow Research Cloud ###Cloud TPUs ###Cloud Platform  ###Google Compute Engine GCE
https://services.google.com/fb/forms/tpusignup/
#account info and links
tpu-help@google.com

#### Self-Driving Car Engineer Nano-Degree
#### ROS Robot OS installation description
http://wiki.ros.org/kinetic/Installation/Ubuntu
#environment vars
printenv | grep ROS
#output:
ROS_ROOT=/opt/ros/kinetic/share/ros
ROS_PACKAGE_PATH=/opt/ros/kinetic/share
ROS_MASTER_URI=http://localhost:11311
ROSLISP_PACKAGE_DIRECTORIES=
ROS_DISTRO=kinetic
ROS_ETC_DIR=/opt/ros/kinetic/etc/ros

#### CNTK V2 1-bit SGD vs Block Momentum Frank Seide

#### CNTK 2 on GDT10CNTK2 VMware
#installed Anaconda3 4.2.0 to c:\local\Anaconda3
#20120131 downloaded b9 CPU-only zip from
https://github.com/Microsoft/CNTK/releases
#zip properties Unblock d/lded scripts
#unzipped to cntk to local\cntk-b9
setx MYCNTKPATH C:\local\cntk-b9
start powershell -executionpolicy remotesigned
#in powershell:
cd C:\local\cntk-b9\Scripts\install\windows
#won´t work (cuz old cmd doesn´t know about envvar?):
#cd $env:MYCNTKPATH\cntk\Scripts\install\windows
#echo %MYCNTKPATH%
.\install.ps1 -AnacondaBasePath c:\local\Anaconda3 #demo / simulation mode
.\install.ps1 -execute -AnacondaBasePath c:\local\Anaconda3
#
Fatal error during script execution!
 System.Management.Automation.RuntimeException: Running 'start-process  env update --file "C:\local\cntk-b9\Scripts\install\windows\conda-windows-cntk-py35-environment.yml" --name "c:\local\Anaconda3\envs\cntk-py35"' failed with exit code [1]

#if not MSMPI and Anaconda: UAC kicks in after Anaconda d/l with MSMPI and half dozen times with Anaconda install!
#c:\repos\CNTK (capitalized) in git "detached head state",
#means one can make changes...
#### Installer:
#To activate the CNTK Python environment and set the PATH to include CNTK, start a command shell and run
C:\local\cntk-b9\Scripts\cntkpy34.bat
#install forced C:\local for Anaconda instead of a subdir to C:\cntk, where the installation was started from
#C:\local is referenced twice in C:\cntk\scripts\cntkpy34.bat
#Moved Anaconda3-4.1.1-Windows-x86_64 from local to cntk; may be important for uninstall to move it back
#python examples are in in c:\repos\cntk\bindings\python\examples
#cd c:\repos\CNTK\Tutorials
#set up path and and env with cntkpy.bat in new cmd and start Jupyter notebook with jn.bat

#### cntk 2 GPU 1bit-SGD cntk v2 GPU 1bit-SGD on G10
#cmd:
cd c:\dl\cntk\Scripts\install\windows
#install (-Execute:$false for test mode):
install.bat -AnacondaBasePath c:\dl\Anaconda3
#set path for cntk
C:\dl\cntk\scripts\cntkpy35.bat

#### Python
#debug
python -m pdb script.py

#### Python Virtualenv
#see http://docs.python-guide.org/en/latest/dev/virtualenvs/
#creates a copy of python executables in neon/.venv
. .venv/bin/activate #activates .venv2
#versions, depending on env set
pip list

#### anaconda ###python
#continuum.io
#### to keep Anaconda current, in Linux #Windows console
source activate root #activate root #"base" only valid / displayed as "base" on Windows
conda update conda
#### numba CUDA-optimizing compiler
conda install numba
conda update --all
conda update anaconda-navigator
conda install navigator-updater

#### python intel ###intel distribution python
#software.intel.com/machine-learning/deep-learning
#anconda.org/intel
#contrary Intel Frank Schlimbach conda is NOT installed, so I installed
#Anaconda 4.3 w Python 3.6 from https://www.continuum.io/downloads
bash Downloads/Anaconda3-4.3.0-Linux-x86_64.sh
conda config --add channels intel
#did not use suggested conda install intelpython3_full w/o env
#from https://software.intel.com/en-us/articles/using-intel-distribution-for-python-with-anaconda
conda create -n idp intelpython3_full python=3
source activate idp #conda activate idp #says conda after install on G10
conda upgrade intelpython3_full
source deactivate
conda remove -n idp --all

#### python ##jetson pip missing
sudo apt-get install python-pip
pip install python-opencv #?

#### ipython notebook ###Jupyter notebook
sudo apt-get -y install ipython ipython-notebook
sudo -H pip install --upgrade pip #9.0.1 or 8.1.2
sudo pip install --upgrade pip #worked, but:
#/home/gy/.cache/pip' or its parent directory is not owned by the current user
sudo -H pip install jupyter #server: jupyter notebook client: localhost:8888
jupyter notebook --no-browser

#### IDLE ###python IDE for other projects
sudo apt install idle


#### uninstall cntk remove cntk
pip uninstall cntk

**********************************
#set path to cntk and activate Anaconda
c:\local\cntk\scripts\cntkpy34.bat
#20161204
C:\dl\cntk\scripts\cntkpy34.bat
#20161226
C:\dl\cntk-b7\scripts\cntkpy34.bat
#*********************************

#run an example just for test
cd c:\local\cntk\Tutorials\NumpyInterop
#20161204
cd c:\dl\cntk\Tutorials\NumpyInterop
#20161226
cd c:\dl\cntk-b7\Tutorials\NumpyInterop
python FeedForwardNet.py

#### jupyter notebook ipython - run tutorials
cd c:\local\cntk-b7\Tutorials
#20161226
cd c:\dl\cntk-b7\Tutorials
jupyter notebook --no-browser
#jupyter notebook ipython directories and search paths
jupyter --paths #outputs:
#config:
C:\Users\gy\.jupyter #?
C:\local\Anaconda3-4.1.1-Windows-x86_64\envs\cntk-py34\etc\jupyter #! json
C:\ProgramData\jupyter #?
#data:
C:\Users\gy\AppData\Roaming\jupyter #!
C:\local\Anaconda3-4.1.1-Windows-x86_64\envs\cntk-py34\share\jupyter #nbextensions
C:\ProgramData\jupyter #?
#runtime:
C:\Users\gy\AppData\Roaming\jupyter\runtime #!


#### cntk 2 on gu1604 128 GB USB
#un-tar .tar.gz to ~
cd cntk/Scripts/install/linux
./install-cntk.sh --py-version 35
#Downloads/cntk-b7-install-protocol-20161228.txt

**************************
#Activate CNTK environment
source "/home/username/cntk/activate-cntk"
#basic test for functionality
python ~/cntk/Tutorials/NumpyInterop/FeedForwardNet.py
#check token
jupyter notebook --no-browser
**************************

#### cntk 2 on 128 GB USB build / make

#### cntk 2 on Ubuntu1604 VMware
#un-tar .tar.gz to ~
cd cntk/Scripts/install/linux
./install-cntk.sh
#warning about PYTHONPATH
echo $PYTHONPATH
#already screwed up with Robot OS?
#/opt/ros/kinetic/lib/python2.7/dist-packages
PYTHONPATH=/home/gy/anaconda3
#### install protocol (Python commands??):
#To activate this environment, use:
source activate /home/gy/anaconda3/envs/cntk-py34
#To deactivate this environment, use:
source deactivate
#To activate the CNTK environment, run
source "/home/gy/cntk/activate-cntk"


#### neon 1.8.1 nervana on Ubuntu1604 VMware Python 2
https://neon.nervanasys.com/docs/latest/installation.html#requirements
#### installed all kinds of dependencies (also OpenCV), but not yet ffmpeg, OpenBLAS (multi-threading)
#OpenCV
sudo apt-get install libopencv-dev python-opencv
#ffmpeg latest by maintainer
sudo add-apt-repository ppa:jonathonf/ffmpeg-3
sudo apt update && sudo apt install ffmpeg libav-tools x264 x265
#clone neon
git clone https://github.com/NervanaSystems/neon.git
cd neon
make
#Python 2 Virtualenv
#see http://docs.python-guide.org/en/latest/dev/virtualenvs/
#creates a copy of python executables in neon/.venv
. .venv/bin/activate #activates .venv2
#test - no prepend with neon or python necessary:
examples/mnist_mlp.py #worked!
#install Jupyter notebooks to the venv
pip install ipython jupyter matplotlib
#ipython jupyter notebooks
https://github.com/NervanaSystems/meetup
deactivate

#### neon 1.8.1 on Ubuntu 16.04 128 GB
#Anaconda install
http://neon.nervanasys.com/index.html/installation.html#anaconda-install
conda create --name neon pip
#don't forget later:
source activate neon
git clone https://github.com/NervanaSystems/neon.git
cd neon && make sysinstall
conda install ipython jupyter matplotlib
#...
source deactivate

#### theano Anaconda 4.3.0 install on Ubuntu16042 Python 3.6
cd Downloads
bash Anaconda3-4.3.0-Linux-x86_64.sh
conda create -n theano
source activate theano
pip install Theano
conda install pydot-ng
conda install ipython
pip install keras
#Successfully installed keras-1.2.2 numpy-1.12.0 pyyaml-3.12 scipy-0.18.1 theano-0.8.2


#### pytorch CPU 0.1.9-py36_2 on Ubuntu1604Intel http://pytorch.org/
#conda create -n envName [packageName]
conda create -n pytorch
source activate pytorch
#### pytorch CPU
conda install pytorch torchvision -c soumith
#### pytorch CUDA 8 python 3.6
conda install pytorch torchvision cuda80 -c soumith
#don´t conda install ipython, but:
conda install jupyter
mkdir pytorch
cd pytorch
git clone https://github.com/pytorch/examples.git
git clone https://github.com/pytorch/tutorials.git
#### pytorch usage w docker autostarting w Intel DL SDK Training Tool:
#release Training Tool container 8080 and jupyter ports on Ubuntu1604Intel only:
docker stop 2240e8ee3e44 -t 0
sudo systemctl stop docker
source activate pytorch
#additionally for jupyter on VM and 128 GB stick 2:
export PATH="/home/gy/anaconda3/envs/pytorch/lib:$PATH"
jupyter notebook --no-browser


#### Deep Learning SDK 1.0.520 ###Intel
#### Training Tool install incl Docker
sudo /home/gy/Downloads/dl-sdk-training-tool-1.0.520/install_training_tool.sh
#added gy to Docker users after reading install log
sudo usermod -aG docker gy
#Training Tool start
docker exec -it trainingtool sh -c "ls -l /workspace"
#browser
localhost:8080
#### Ubuntu daemon config systemd (14.04 upstart) /etc/systemd, /etc/rcN.d
#### systemd-manager systemd-GUI-deb https://github.com/mmstick/systemd-manager
#list daemons on Ubuntu
sudo systemctl
sudo systemctl is-active docker
#docker start at boot
sudo systemctl enable docker
#does not work though it calls sysV:
sudo systemctl disable docker
#try with sysV
sudo apt install sysv-rc-conf
#after disabling docker with systemctl, runlevels are unchecked in sysv-rc-conf:
sudo sysv-rc-conf
#no-go too:
sudo update-rc.d docker remove
sudo sysv-rc-conf -P
sudo systemctl start docker


#### Google Chrome on Ubuntu
sudo dpkg -i Downloads/google-chrome-stable_current_amd64.deb #simply double-click!!
google-chrome
#### gimp on Ubuntu
sudo add-apt-repository ppa:otto-kesselgulasch/gimp
sudo apt update
sudo apt-get install gimp


#### exFAT on Ubuntu
sudo apt-get install exfat-fuse exfat-utils
#access sd card in VMware: VM settings > Hardware tab Add >
 IDE > Use physical disk > Use entire (> rename vmdk? none for physical

#### Ubuntu package install when already installed: x set to manually installed
sudo apt-mark auto x

#### Ubuntu 16.04
#### display / graphics driver on XPS
#identify graphics adapter / card
lspci | grep VGA #lists Intel Skylake
#X driver
glxinfo #lists driver details, but only Nvidia
#gedit /etc/X11/xorg.conf
#lists both adapters with details:
sudo lshw -C video

#### windows 10 Windows-Subsystem für Linux WSL file system location
%localappdata%\Lxss\rootfs #=
C:\Users\gy\AppData\Local\lxss\rootfs #e.g. on G10
#actual user home /home/gy:
C:\Users\gy\AppData\Local\lxss\home
#and NOT in
C:\Users\gy\AppData\Local\lxss\rootfs\home
#actual root home
C:\Users\gy\AppData\Local\lxss\root
#and NOT
C:\Users\gy\AppData\Local\lxss\rootfs\root

#### raspberry ###pi ##raspbian debian 8 jessie w pixel desktop WLAN 10.0.0.8
cat /etc/os-release #raspbian version
#### Raspbian Pixel standard user: pi (not gy) pw usual Linux
sudo apt-get update
sudo apt-get dist-upgrade
sudo apt-get autoremove #NOT clean as suggested in raspberrypi.org
sudo apt-get install samba samba-common-bin #smb://g10 hot domain hotmail.com
sudo nano /etc/samba/smb.conf #share Downloads folder:
[PiShare]
comment=Raspberry Pi Share
path=/home/pi/Downloads
browseable=Yes
writeable=Yes
only guest=no
create mask=0777
directory mask=0777
public=no
#end text; add user pi to smb network users, domain raspberry:
sudo smbpasswd -a pi

#### virtualenvironment python2 on raspi
sudo pip install virtualenv virtualenvwrapper
$ sudo rm -rf ~/.cache/pip
#~/.profile - append to end:
#virtualenv and virtualenvwrapper
export WORKON_HOME=$HOME/.virtualenvs
source /usr/local/bin/virtualenvwrapper.sh
#to switch to virtual environment NOT DONE
source ~/.profile
workon Sunfounder #NOT DONE
#spyder on #raspbian
sudo apt install spyder #not pip

#### OpenCV on raspi according to
https://www.pyimagesearch.com/2016/04/18/install-guide-raspberry-pi-3-raspbian-jessie-opencv-3/
#cmake
cd ~/Downloads/opencv-3.4.1/
mkdir build
cd build
cmake -D CMAKE_BUILD_TYPE=RELEASE \
    -D CMAKE_INSTALL_PREFIX=/usr/local \
    -D INSTALL_PYTHON_EXAMPLES=ON \
    -D OPENCV_EXTRA_MODULES_PATH=~/Downloads/opencv_contrib-3.4.1/modules \
    -D BUILD_EXAMPLES=ON ..
make #took 3.5h on raspi w 1 core
sudo make install

#### GPIO from terminal #GPIO18 PCM_CLK pin12
sudo echo "17" > /sys/class/gpio/export #prepare GPIO17
sudo echo "out" > /sys/class/gpio/gpio17/direction #write - or read "in"
sudo echo "1" > /sys/class/gpio/gpio17/value
#NOT needed to read! Changes value! #sudo echo "in" > /sys/class/gpio/gpio17/direction
cat  /sys/class/gpio/gpio17/direction
cat  /sys/class/gpio/gpio17/value

#### GPIO with ##wiringPI #prep:
git clone git://git.drogon.net/wiringPi
cd wiringPi
./build
#terminal sample in #wiringPi
gpio export 17 out #no sudo required?! Exporting resets to 0!
gpio -g write 17 1
gpio -g read 17

#### PiGPIO http://abyz.me.uk/rpi/pigpio/
rm pigpio.zip
sudo rm -rf PIGPIO
wget abyz.me.uk/rpi/pigpio/pigpio.zip #d/l to ~
unzip pigpio.zip #unzips to ~/PIGPIO/
cd PIGPIO
make #gcc
sudo make install #results in:
#/opt/pigpio/cgi /usr/local/include/*.h /usr/local/lib/*.so /usr/local/bin
#/usr/local/lib/python3.4/dist-packages/pigpio.py

#### PWM Pulse Width Modulation; code see F:\Prg\RaspberryPi\PWM.txt
#p.102 web.stanford.edu/class/cs140e/docs/BCM2837-ARM-Peripherals.pdf refers to BCM2835!
#2 hardware_PWM channels on ALT pin pairs on the PI 3 model B:
#ALT0 GPIO12 & 13, pins 32 & 33; Alt5 GPIO18 & 19, pins 12 & 35 #DIFFERENTLY FORMULATED:
#ALT5 channel 0 #PWM0 GPIO18 PCM_CLK pin 12 6th pin outer edge; PWM1 GPIO19 pin 35 #DIFFERENTLY FORMULATED:
#PWM0 can use GPIOs 12, 18. Compute Module: 40 & 52. Only GPIO12 (pin 32) and 18 (pin 12) are available on the connector
#PWM1 can use GPIOs 13, 19. Comp Module: 41, 45 and 53. Only GPIO13 (pin 33) is available BUT shared w audio!
#Look for too: clk_pwm, pwm_chn, PWM Address Map, PWM_RNGi
#### servo typical values / ranges
#pulses per second / pulse repetition rate / refresh rate: pulse every 20 ms = 50 Hz / 40 - 200 Hz
#rotation angle = pulse width; e.g. 1.5 ms pulse = neutral = 90°, 0.5 ms = 0° 2.5 ms = 180°
#duty cycle maybe RELEVANT for ElectronicSpeedControl, but NOT for servo position / Periodenlänge / percentage of pulse-on / formula: pulse width / pulse frequency * 100: dc 25% = 1.5 ms pulse every 6 ms, dc 6% = 1.5 ms pulse every 25 ms

#### PiGPIO abyz.me.uk/rpi/pigpio/python.html#hardware_PWM
#def: hardware_PWM(gpio, PWMfreq, PWMduty)
pi.hardware_PWM(18, 800, 250000) # 800Hz 25% dutycycle
#see too:
get_mode(gpio) #for hw-GPIO use gpio=18or19 ALT5 or =12or13 ALT0, pins 12or35 or 32or33; gpio > 40 only available on Computer Module
#returns 0 = INPUT or 1 = OUTPUT or 2 = ALT5 or 3 = ALT4 or 4 = ALT0 or 5 = ALT1 or 6 = ALT2 or 7 = ALT3
get_servo_pulsewidth(user_gpio)
#example:
pi.set_servo_pulsewidth(4, 525)
print(pi.get_servo_pulsewidth(4))
#returns 525

#### AWS #Greengrass #Squeezenet model for inference on #RasPi; too big: #AWS DeepLens
#MXnet pre-built for (Sagemaker on) Jetson, RasPi
#YouTube video at ca 18": Run ML Models at the Edge with AWS Greengrass ML
#RasPi camera access: /dev/vcsm and /dev/vchiq #Sense HAT (for LEDs) at /dev/fb1 (fbOne)


#### CSI camera IF Pi #MIPI #CSI Camera Serial Interface 15 pin

#### AADC 2018 ###Audi
#### gazebosim.org install:
curl -ssL http://get.gazebosim.org | sh


#### sunfounder.com
git clone https://github.com/sunfounder/Sunfounder_Smart_Video_Car_Kit_for_RaspberryPi.git
sudo apt update
sudo apt upgrade
sudo apt install python-dev
sudo apt install python-smbus #already latest v
#sudo raspi-config # > Advanced > I2C doesn´t work. use config GUI to enable
cd /home/pi/Sunfounder_Smart_Video_Car_Kit_for_RaspberryPi/server
sudo python cali_server.py
#part 2 **on PC**
conda create -n sunfounder python=2.7
source activate sunfounder
cd \dl\sunfounder
idle #open client/cali_client.py; Run > Run Module
#/home/pi/Sunfounder_Smart_Video_Car_Kit_for_RaspberryPi/server/config
#### USB camera Sunfounder GEMBIRD
lsusb #Bus 001 Device 004: ID 1908:2311 GEMBIRD
ls /dev/vid* #/dev/video0
#MJPEG-streamer dependencies
sudo apt install subversion #sudo apt-mark auto subversion #to revert it to auto-install
sudo apt install lib4l-dev
sudo apt install libjpeg8-dev
sudo apt install imagemagick
#MJPEG-streamer Sunfounder compile
cd /home/pi/Sunfounder_Smart_Video_Car_Kit_for_RaspberryPi/mjpg-streamer/mjpg-streamer
sudo make USE_LIBV4L2=true clean all #doesn´t work, but w/o libv4l2 it does:
sudo make USE_LIBV4L2=false clean all
sudo make DESTDIR=/usr install
#MJPEG-streamer video server
sudo sh start.sh
#control car
cd /home/pi/Sunfounder_Smart_Video_Car_Kit_for_RaspberryPi/server
sudo python tcp_server.py

#### lane detection #Johannes Kaisinger #Hannes
#### as.cmd activate sunfounder on G10 Windows Anaconda python 2
activate sunfounder
pip install opencv-python #installs numpy too
conda install spyder #& dependencies for Python 2
#G10
cd C:\dl\Sunfounder\G\lane
python lane_detect.py

#### navigable terrain


#### Arduino ##Genuino
#### Arduino IDE C:\Users\gy\AppData\Local\Arduino15\preferences.txt
#Sketch > Include Library > Add ZIP Library F:\Prg\Arduino\AdeeptZIP\Adeept_Libraries #ends up in:
#C:\Users\gy\Documents\Arduino\libraries\RF24
#RC: FT232R USB UART einsatzbereit COM6 9600/8/no parity/1 stop/keine Flusssteuerung
#Tools > Get Board Info: BN: Unknown board VID: 0403 PID: 6001 SN: Upload any sketch to obtain it
#Car: Serielles Gerät COM7 eingerichtet  9600/8/no parity/1 stop/keine Flusssteuerung
#Tools > Get Board Info: BN: Arduino/Genuino Uno VID: 2341 PID: 0043 SN: 55736313038351406061

#### Enhancement ideas:
#if-else instead of 2 ifs for mode change in RC would be cleaner
#steering & fwd bwd on same stick possible!?
#use only one button (B or C) as toggle for RC & Auto mode
#switch LED to YMC by combinations of RGB
#PWM-control the LED brightness & hue


#### RTAndroid ###Android
https://git.embedded.rwth-aachen.de/rtandroid/downloads/raspberry-pi/
#hdmi_mode in boot/config.txt; table of modes:
https://www.raspberrypi.org/documentation/configuration/config-txt.md
#hdmi_mode for hdmi_group=2 (DMT = Display Moni Timing)
#(better modes (resolution,..) than hdmi_group=1)
82	1920x1080	60Hz	1080p
69	1920x1200	60Hz

#### Android Things
cd C:\workspaces\sdks\android\platform-tools
adb connect 10.0.0.14

#### Windows IoT 14931
#renamed to gwiot; default initial p@ssw0rd is now iotNNxxx

#### jetson tx2 named tegra-ubuntu; 5.5-19.76 V, static Ethernet IP 10.0.0.20 on router
#tightvnc unnecessary (vino vnc installed)
#Search Your Computer for Desktop Sharing to configure Vino
#and Software dconf to ^F / uncheck require-encryption
#sudo nano /etc/systemd/system/tightvncserver.service #file doesn´t exist
#ssh -L 5901:127.0.0.1:5901 -N -f -l username server_ip_address #ssh #tunnel for #vnc

#### jetson ##jetpack 3.2 with L4T R28.2 install 20180318 using Dell Ubuntu 16.04
#check OS version
head -n 1 /etc/nv_tegra_release #where R27 (release), Revision: 0.1 == 27.1
#user nvidia pw nvidia changed to usual; user ubuntu pw ubuntu changed to usual
mkdir j4t
cd j4t
../Downloads/JetPack-L4T-3.2-linux-x64_b196.run
#20170331 host install only, incl extra CUDA 9.0.252-1 #in addition to /usr/local/cuda-8.0?
#Install packages VisionWorks, CUDA Toolkit, Compile CUDA samples, TensorRT, OpenCV for Tegra, Multimedia API pack, cuDNN
#OpenCV install problem; OpenCV found in /usr/bin, include, share; removed w Synaptica Package Manager
#after setup right-click on desktop > Open Terminal Window
#switch from FHD to 1920x1200
xrandr #to list available resolutions; then
xrandr --output HDMI-0 --mode 1920x1200 --rate 59.95
#open System Settings: wiggle resolution to make it stick for sure; add De kbd; change Settings
#Search your Computer to add gedit, video, music
#Ubuntu Software: browser

#### VisionWorks Nvidia #OpenVX lib Khronos.org
/usr/lib/libvisionworks.so,...
/usr/share/visionworks/sources/ &cmake/
/usr/share/doc/libvisionworks
~/VisionWorks-SFM-0.90-Samples/
#### CSI vs USB cameras - CSI: Leopard Imaging Inc IMX185
#libargus TX1 camera API f MIPI.org CSI Camera Serial Interface to ISPs Image Signal Processors
#V4L2 Video4Linux2 f USB cameras linuxtv.org


#### sequence analysis and phylogenetics Gundula Povysil 365.062 Fr 6.10. then 10.11. weekly
#### spyder IDE in Anaconda
conda upgrade spyder
#### python tutorial seq
dl = r'C:\dl' #raw string, else escape: dl = 'C:\\dl'
'abc'.count('b'); 'abc'.replace('b', 't'); 'abc'.upper(); 'abc'[1:]; 'abc'[-1:] #neg from eos
str(12);


#### gitlab-ctl GitLab server Ubuntu install
ssh-keygen #all default
sudo apt-get install -y curl openssh-server ca-certificates
#postfix: edit /etc/postfix/main.cf (and others) as needed.
#To view Postfix configuration values, see postconf(1).
After modifying main.cf, be sure to run '/etc/init.d/postfix reload'
sudo apt-get install -y postfix #mail-name is Ubuntu
curl https://packages.gitlab.com/install/repositories/gitlab/gitlab-ee/script.deb.sh | sudo bash
sudo apt-get install gitlab-ee
#GitLab was unable to detect a valid hostname for your instance.
#configure URL for instance by setting 'external_url'
sudo nohup gedit /etc/gitlab/gitlab.rb
#temporarily changed to 127.0.0.1:8888
#Then, you can start your GitLab instance by running the following command:
sudo gitlab-ctl reconfigure
#For a comprehensive list of configuration options please see the Omnibus GitLab readme
https://gitlab.com/gitlab-org/omnibus-gitlab/blob/master/README.md
#
sudo apt-get install sysv-rc-conf #installed to check for autostart, but gitlab no-show
sudo gitlab-ctl status #just check
sudo gitlab-ctl stop #all services
#### purge gitlab-ee not executed
sudo apt purge gitlab-ee


#### AI Ue
#### GitLab account hot username k08356354 pw JKU https://unicorns.cp.jku.at/u/k08356354
#gitlab uses git; no GitLab install necessary
#### Exercise assignment0 initially on Ubuntu, secondary Windows the same
#Win git bash
cd /c/workspaces/workspaces/ai
#Ubuntu
mkdir ai #created as an afterthought on Ubuntu and dir exercise moved there after clone
cd ai #cd aio #Eclipse-Oxygen
git clone git@unicorns.cp.jku.at:group0043/exercise.git
cd exercise #not in presentation slides! on Windows bash #cd /c/workspaces/workspaces/ai/exercise
#bash says: /c/workspaces/workspaces/aio/exercise (master)
#set a remote repository called upstream
git remote add upstream git@unicorns.cp.jku.at:aiws17/exercise.git
#first we need to retrieve the state of the remote repository which we called upstream
git fetch upstream
#list all available branches with
git branch -a
#git checkout assignment0 #didn´t work, but from email:
git checkout -b assignment0 --track upstream/assignment0

#introduce separate branches, for you and your partner not to step on each other’s toes
#eg assignment0_<yourname> for example
https://git-scm.com/book/en/v2/Git-Branching-Basic-Branching-and-Merging

#### git workflow
#update your local repository to the newest commit
git pull #to update assignment not necessary
git checkout assignment0 #?
Already on 'assignment0'
Your branch is up-to-date with 'upstream/assignment0'.

#### git commands
#show where the dir was cloned from
git remote show origin
#file / dir name w dot in front .name
ren name .name
#remove git info from dir Linux ##Windows?
rm -rf .git ##rmdir /S /Q .git #rmdir .git

#### github.io ##ai-bits.github.io ##atom for edit
cd C:\xampp\htdocs\ai-bits.github.io
git pull

#### JekyllRB.com on ubuntu1604 VM #jekyll is a #ruby #gem; prereq:
#ruby -v #2.3.1 #gem -v #2.5.2.1 #gcc -v #5.4.0 #g++ -v #returns gcc #make -v #4.1
sudo apt install ruby-dev
#gedit .bashrc; add:
export GEM_HOME=$HOME/gems
export PATH=$HOME/gems/bin:$PATH
#activate .bashrc settings w:
source ~/.bashrc #then
gem install jekyll bundler tree #jekyll -v #3.7.3 #gem list jekyll
#https://jekyllrb.com/docs/installation/
#also: bundle update jekyll #or: gem update jekyll #and: gem update --system #for latest gems
#firewall status check
sudo ufw status #inactive on Ubuntu1604, so not necessary to
#sudo ufw allow 4000 #jekyll port


#### jekyll website gue52.github.io on ubuntu1604 VM:
jekyll new gue52github.io #w default minima theme
#...
#YAML Front Matter for Jekyll begins & ends w ---, e.g.
---
layout: post
title: Google Tensorflow and MS CNTK on One Machine
---
jekyll serve #--host=IP


#### Eclipse-Oxygen (latest as of 20171012) setup Ubuntu1604
#download installer, un-tar & right-click Run eclipse-inst
#~gy/eclipse/java-oxygen


#exercise assignment0 report 4 Theory complexity O e.g. wikipedia hash table

#hand in:
git push -u origin assignment0
#necessary for report locally?
git add reports/report.pdf
git commit -a -m 'changes to report' #to make it pushable

#### assignment1 Windows or both #Ubuntu
cd /c/workspaces/workspaces/ai/exercise #cd ~/ai/exercise
git fetch upstream
#to get assignment1 in exercise folder:
git checkout assignment1
#feedback Win
#Switched to a new branch 'assignment1'
#M       src/at/jku/cp/ai/search/algorithms/RS.java
#Branch assignment1 set up to track remote branch assignment1 from upstream.
#feedback Ubuntu
M	.gitignore
M	src/at/jku/cp/ai/search/algorithms/RS.java
Branch assignment1 set up to track remote branch assignment1 from upstream.
Switched to a new branch 'assignment1'

#### assignment1 Pauls uploads
cd /c/workspaces/workspaces/aio/exercise
git fetch upstream
git branch -a
#git pull origin assignment1 #not right; see below; no idea why not originSLASHassignment1 or w/o origin?
#renders: error: Your local changes to the following files would be overwritten by merge:
  #src/at/jku/cp/ai/search/algorithms/BFS.java
#kill local changes and pull Paul's changes w his commit comment:
git reset --hard origin/assignment1
HEAD is now at 1dde6dd level added - costs missing - algos working

#### competition project in Eclipse Oxygen
cd /c/workspaces/workspaces/aio
git clone git@unicorns.cp.jku.at:group0043/competition.git

#### Harman ###Samsung Christoph Neumann NLU
```