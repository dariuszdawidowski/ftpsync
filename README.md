# ftpsync
Command-line tool to smart-synchronizing local directory with remote FTP.

Simple and elegant, written in Python without 3rd-party dependencies.

Usage:
======

ftpsync user:pass@ftp.address.url/remote/directory/

Args:
=====

-c '...': run raw ftp command instead of sync (use ; for multiple commands)

--delete: delete non-existing files on server side

Ignored files:
==============

Put .ftpignore file in the source directory.

Example content:

ignored_file_name.ext

ignored_directory_name

also_you_can_use_*_wildcard

use hash # for comments

Meta files:
===========

.ftpsync is automatically created in every ftp directory with metadata syncing info

Have to sync hundrets of sites?
===============================

You can create .csv file and simple bash script:

```bash
#!/bin/bash

while IFS=, read -r user pass host remotedir
do
    ftpsync $user:$pass@$host/$remotedir --delete
done < servers.csv
```
Example contents of servers.csv:
```csv
john,p4ssw0rd,ftp.host.com,/public_html/sites/johnsite
jack,p4ssw0rd2,ftp.host2.com,/public_html/sites/jacksite
```
