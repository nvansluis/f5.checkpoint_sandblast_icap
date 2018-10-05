# f5.checkpoint_sandblast_icap
iApp template to integrate F5 BIG-IP with Check Point SandBlast ICAP server

### Enable SandBlast ICAP server
Login to export mode and start the ICAP server on the TEX appliance or security gateway.
<pre>
[Expert@cp-fw-01:0]# icap_server start
cpwd_admin: 
Process CICAP started successfully (pid=31792) 
[Expert@cp-fw-01:0]# 
</pre>

Check if the ICAP processes are running.
<pre>
[Expert@cp-fw-01:0]#  ps -def |grep icap
admin    31792  4631  0 19:19 ?        00:00:00 c-icap -N -f /opt/CPsuite-R77/fw1/c-icap/etc/c-icap.conf
admin    31813 31792  0 19:19 ?        00:00:00 c-icap -N -f /opt/CPsuite-R77/fw1/c-icap/etc/c-icap.conf
admin    31820 31792  0 19:19 ?        00:00:00 c-icap -N -f /opt/CPsuite-R77/fw1/c-icap/etc/c-icap.conf
admin    31826 31792  0 19:19 ?        00:00:00 c-icap -N -f /opt/CPsuite-R77/fw1/c-icap/etc/c-icap.conf
admin    31931 31651  0 19:20 pts/1    00:00:00 grep icap
[Expert@cp-fw-01:0]# 
</pre>

Enable ICAP logging.
<pre>
[Expert@cp-fw-01:0]# tecli advanced remote emulator logs enable
remote emulator logs set to enabled successfully
[Expert@cp-fw-01:0]# 
</pre>

Also make sure that your firewall rules allow access to the ICAP server port 1344/TCP on the TEX appliance or security gateway.

### Prepare the F5 BIG-IP
#### Import the f5.checkpoint_sandblast_icap iApp template
#### Create a new Application with use of the f5.checkpoint_sandblast_icap iApp template
#### Add the newly created Request/Response Adapt profiles

### Notes
This iApp template is based on the OPSWAT F5 iApp template that can be found here: https://github.com/OPSWAT/F5-iApp
