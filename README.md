Example arch-bootstrap playbook
=========

Example playbook utilizing the arch-bootstrap role 

Preparation
------------
After cloning this repository run galaxy the fetch the arch-bootstrap role:
<pre><code>
ansible-galaxy install -r requirements.yml --roles-path roles
</code></pre> 

This will create the roles folder and fetches the arch-bootstrap role.
This action only needs to be performed once, as the playbook will handle the ansible-galaxy run.

Installing
------------
To install a new arch box do the following:
1.  boot the arch installation iso
2.  Perform the following actions in the console:
- start sshd
- set root password
- install python2
<pre><code>
root@archiso ~ # systemctl start sshd
root@archiso ~ # passwd root
New Password: 
Retype: password updated successfully
root@archiso ~ # pacman -Sy python2
3. check the ipaddress of the new box
<pre><code>
ip a
