Role Name
=========
Snockow6.Openzfs
This Role will install the latest version of openzfs and its Dependencies. it will then create or import the zfs pools defined in the variables and create datasets also defined in the variables.


Requirements
------------

This role requires to be used on debian 10, fedora 32 and up, centos 8 and up and ubuntu 18.04.


Role Variables
--------------

name: 'Tank' #Name for the pool
mountpoint: '/Tank' #Where the pool will be mounted on the filesystem
mode: 'single'  #the raid mode for the pool
state: 'present' #present will create the pool, absent will destry the pool
options: ['ashift=12'] #Add any extra options that maybey required for the pool"
import: 'false' #Used to try import an existing pool
devices: ['sdd', 'sdc'] #the devices used in creation of zfs pool

zfs_datasets is for creating zfs folders with the option for extra settings and snapshoting capabilities.

name: 'shares/ISO' #name of dataset and the previous dataset if nested
pool: 'Tank' #name of zfs pool it is on
state: 'preset' #if present will make sure it exists otherwise deletes it
properties: #used to add extra properties like sharesmb on for dataset to be shared by samba if installed
  sharesmb: on

Dependencies
------------

This is a self contained Role and will install all Dependencies to run Openzfs.

Example Playbook
----------------

Including an example of how to use your role (for instance, with variables passed in as parameters) is always nice for users too:

    - hosts: servers
      vars_files:
        - vars/zfs.yml
      roles:
         - snockow6.openzfs

License
-------

BSD

Author Information
------------------

An optional section for the role authors to include contact information, or a website (HTML is not allowed).
