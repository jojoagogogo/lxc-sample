lxc-sample
==========

lxc sample instance 

## quick start for centos

### 1. lxc install
<pre>
echo "
[dag]
name=Dag RPM Repository for RHEL6/CentOS6
baseurl=http://ftp.riken.jp/Linux/dag/redhat/el6/en/\$basearch/dag
enabled=1
gpgcheck=1
" > /etc/yum.repos.d/dag.repo
</pre>
  * yum install bridge-utils
  * yum -y install lxc-devel lxc-doc lxc-libs lxc-templates lxc

### 2. host bridge network

 * cat /etc/sysconfig/network-scripts/ifcfg-br0 
<pre>
DEVICE="br0"
BOOTPROTO="static"
ONBOOT="yes"
IPADDR=192.168.1.1
NETMASK=255.255.255.0
TYPE=Bridge
</pre>

 * cat /etc/sysconfig/network-scripts/ifcfg-eth0 
<pre>
DEVICE="eth0"
ONBOOT="yes"
BRIDGE=br0
</pre>

### 3. mount cgroup
<pre>
echo "cgroup      /cgroup          cgroup  defaults        0 0" >> /etc/fstab
</pre>
  * mount -a

### 4. git clone https://github.com/jojoagogogo/lxc-sample.git
  * cd lxc-sample
  * mv lxc01 /var/lib/lxc/

### 5. start lxc
  * lxc-start -n lxc01

### 6. login 
  * root 
  * password lxc 

### 7. ssh login
  * ssh root@192.168.1.101

### 8. stop lxc 
  * lxc-stop -n lxc01

### 9. modify lxc config
  * edit lxc config file for your environment :)

