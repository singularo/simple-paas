
## BACKBLAZE setup

Simple paas uses BACKBLAZE B2 as a backup/restore destination.
This requires a little setup and authorization.

These are some notes on the tools used. Note the host_setup script
performs these steps for you.

### B2 command

The b2 command allows easy, scripted creation of buckets and keys.

Installation instructions for the B2 command line are available here:
https://www.backblaze.com/b2/docs/quick_command_line.html

Some b2 operations require a BACKBLAZE 'root' level account.
A dedicated account should be created for each installation and then run
the command to store the credentials on the local machine.
```
b2 authorize-account
```

### under the hood

What the B2 command is for creating a new bucket and key for each new
site launched. This is then available for the backup/restore
commands.

These are the commands that are run.

Create a backup bucket for storage.
```
b2 create-bucket sample-website allPrivate
```

Create a key for authentication.
```
b2 create-key --bucket sample-website sample-website-key \
   listFiles,listBuckets,readFiles,shareFiles,writeFiles,deleteFiles
```



