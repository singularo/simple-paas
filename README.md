
# Simple paas

- An Anti-Kubernetes, Anti-Galera. Anti enterprise lightweight hosting PAAS.
- Designed to be used on cattle-like hosts that are easily re-created.
- Not designed for mission critical websites.

## What?

These few scripts that make it relatively easy to deploy and update websites in containers.

Its created as a fun way to explore containers and expand on basic docker usage so that the next step up is a Kubernetes cluster.

As its just shell scripts, it should be easy to understand.

Commands must be run as root/with sudo on the host itself.

Automated backups are easy to perform so that when there is a disaster, a complete new host with all contents from the most recent backup can be spun up in minutes.

## How to get started

- Checkout SETUP.md to get started setting up a host.
- Checkout DEVELOP.md to get started building images for sites.

### Repository

In order to deploy with this system, they need to be built with docker images. Gitlab supports this workflow well, with the built in registry and easy ability to build docker images and push to the registry.

### Server

These scripts can run on anything that can run docker and mysql with some resources free.

### Storage

A directory on the server stores all files related to the sites. Subdirectories owned by each site contain the files for each container.

### Backups

Commands for backing up with tar and restic are included. Tar is simple and simple is best, but there are some advantages to restic for regular automated backups.

## Expanding/making a machine into a cluster!

It might be a fun experiment, but heading down this path will inevitably become excessively complex.

1. Put docker into swarm mode.
2. Setup a separate host as an NFS server, or setup hosts as a gluster server and mount the /sites folder from there.
3. Setup an external mysql server or galera cluster and change the details in /etc/simple-paas/sp_config to point to that server.
4. Add another host.
5. Setup varnish or haproxy on another host as a load balancer.
6. Implement consul or etcd to synchronise things between hosts.
7. Congratulations, you should have just used Kubernetes!
