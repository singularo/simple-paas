
# Simple paas

## Server setup

- Launch an Ubuntu 20.04 server in the cloud or locally with vagrant / virtualbox etc.
- Login to the machine as root
- Clone the simple-paas repository:
  ```
  git clone git@github.com:singularo/simple-paas.git
  cd simple-paas
  ```

- Execute the host setup script (or do the steps in the script yourself manually).
  ```
  EMAIL=bob@test.com REGISTRY=registry.mydomain.com/internal BUCKET=myhosting simple-paas/host_setup
  ```
### The script will:

- Install Docker, mysql, pip, memcache, jq
- Run a test docker container 'hello-world'
- Create required directories
- Apply docker tweaks
- Symlink the simple paas executables into /usr/local/bin
- Set mysql to bind to all ip addresses
- Copy the nginx config tweaks into place
- Copy the example config into /etc/simple-paas and update it
- Login to the docker repository
- Authorise the machine for B2 access
- Create a new bucket in B2 for the backups
- Start the nginx-proxy and nginx-proxy-letsencrypt containers

### Then what?

Checkout COMMANDS.md for details on each provided command and usage.

