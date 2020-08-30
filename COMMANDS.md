
# Simple paas

## Requirements

Each of the commands below uses `short-repository-name`. Where does this come from?

This is the basename of the git repository. For example if the git repository is:
```
git@gitlab.mydomain.com/internal/test1.git
```

Then the docker build stores the image as:
```
registry.your-domain.com/projects/test1
```

Then the `short-repository-name` would be `test1`

## Commands in order of common usage

### sp_start

The start command deploys a new site onto the host. The syntax is:

Usage:
```
sp_start short-repository-name
```

### sp_backup

The backup command performs a complete backup of a site. It performs an sql dump and then  backup the sql and files to the configured B2 bucket. An optional second argument can be specified for manual backup/testing, eg passing bash will start a bash shell with the backup script and variables set.

Usage:
```
sp_backup short-repository-name [bash]
```

### sp_update

When you have done changes/upgrades to a site, and want to deploy the updates, this command will pull the latest docker image, then remove the old one and deploy the new one. There will be a tiny downtime, dependant on the speed of the host.

Usage:
```
sp_update short-repository-name
```

### sp_cron

Used to run whatever cron commands are required for the site.

Usage:
```
sp_cron short-repository-name commands to run
```

So a crontab entry might look like:

```
* * * * * /usr/local/bin/sp_cron test-site drush cron
```

### sp_shell

Usage:
```
ss_shell short-repository-name
```

Drop into a shell with the same environment as the website.

### ss_b2_setup

This is usually run automatically from ss_start. It sets up the BACKBLAZE B2 details for the site (B2 key and restic password).

Usage:
```
ss_shell short-repository-name /sites/short-repository-name
```
