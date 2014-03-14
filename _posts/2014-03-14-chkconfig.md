---
layout: post
category : sysadmin
tagline: "How to list and change services runlevels on a RedHat system"
tags : [service, daemon, runlevel, redhat, sysadmin]
---
{% include JB/setup %}

To list the services and runlevels:
	
	# chkconfig --list

To turn a service "on" in the default runlevels:
	
	# chkconfig <service_name> on

To turn a service "off" in the default runlevels:
	
	# chkconfig <service_name> off

More info: https://access.redhat.com/site/documentation/en-US/Red_Hat_Enterprise_Linux/6/html/Deployment_Guide/s2-services-chkconfig.html
