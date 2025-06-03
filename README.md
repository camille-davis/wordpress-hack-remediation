# Steps to remediate a hacked Wordpress site

## Identify how and when the site was hacked

* Check if any plugins need updating and if any vulnerabilities have been reported.
* Check email logs for suspicious emails.
* Check for modified core files and look up suspicious filenames or code.
* Run a database scan.
* Look at Wordfence logs.

## Remediation

If you can identify the hack date and have backups from before then, restore the backup.

Otherwise, download a fresh Wordpress install. Then:

### Plugins

Go through installed 3rd party plugins and themes. For each, check:
* Is it actually being used?
* When did the last update come out?
* How many active users does it have?

Assess each plugin's safety, then reinstall plugins based on the assessment.

### Child theme

Check each file manually, then reinstall.

### Database

Run a malware scan on the original database.

Remove suspicious users (unknown admins, weird usernames created after hack date...)

Then migrate data to new install.

## Post remediation

* Set up regular backups.
* Reinstall Wordfence and setup rate limiting and alerts.
* Connect Wordfence logs to external storage so you can access them even if Wordfence is deleted.
