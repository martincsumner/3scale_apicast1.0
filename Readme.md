TITLE: Vagrant Image for setting up the NGINX Proxy for 3Scale APICast.
=======================================================================

This project allows you to 'hello world' 3Scale using the 'Self-managed Gateway'

==============
 You will need to go onto the 3Scale portal and configure an API to manage.
 Download the nginx proxy files as a zip - via the link at the bottom of the API >> Integration page.

Prerequisites
=============
A running Vagrant installation - typically virtualbox + vagrant.
You will also need to have Ansible installed.

Installation.
=============
1. Once you have the zipped nginx proxy files generated from the portal then copy them into the following path in this project:

	./roles/nginx_files/files 

2. Having done this then 'vagrant up' from the same directory as the Vagrantfile.

Description.
=============
What does this do?

1. Sets up a Centos VM.
2. Sets up and then installs openresty (the distribution of nginx used by 3scale) via yum.
3. copies over the conf. files for nginx.
4. finally starts nginx

Could you use this playbook to set up a nginx production server? - more or less.
Maybe this will be a following appdev practise project :-)

One last thing....
===================
Make certain that you are calling proxy via the same entered value in the 'public api' section of the portal.

So in otherwords the value that you type to call this proxy might look something like this:

curl -v -X GET "http://192.168.33.10/search?term=beyonce&entity=musicVideo&user_key=7b86fdea742e29594449ab12f0b487c0"

<user_key comes from the admin portal...>


The 'http://192.168.33.10' must appear in your 'Public Base URL' in the api definition within the portal.

Finally
========
Enjoy!

Troubleshooting:

vagrant ssh into the vm and check the logs here:
/usr/local/openresty/nginx/logs


if the 3scale DNS does not resolve correctly from the proxy you will see something like this:
13:43:16 [error] 13261#13261: *10 su1.3scale.net could not be resolved (110: Operation timed out)



