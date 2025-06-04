# Steps to remediate a hacked Wordpress site

## Collect data

Identify how and when the site was hacked:
* Check if any plugins need updating and if any vulnerabilities have been reported.
* Check email logs for suspicious emails.
* Check for modified core files and look up suspicious filenames or code.
* Run a database scan.
* Look at Wordfence logs.

## On existing website

### Credentials

* Log everyone out (reset keys in wp-config.php)
* Reset administrator passwords.
* Remove suspicious users (unknown admins, weird usernames created after hack date...)
* Update hosting credentials.
* Update database credentials.

### Core files

Delete unknown files in core, restore modified files.

### Third party themes and plugins

Update all third party themes and plugins.

### Custom themes and plugins

Compare to reference.

### Database

Scan entries and look especially closely at entries from after the hack date.

## Remediation

### Core files

Download a fresh Wordpress install.

### Third party themes and plugins

Go through third party plugins and themes. For each, check:
* Is it actually being used?
* When did the last update come out?
* How many active users does it have?

Assess each plugin's safety, then reinstall based on the assessment.

### Custom themes and plugins

Reinstall after comparing to reference.

### Database

After scanning original database, migrate data to new install.

## Post remediation

* Set up regular backups.
* Reinstall Wordfence and set up safety procedures, especially:
  * Rate limit or block 404s
  * Rate limit login attempts
  * Send email alerts if Wordfence is disabled or scan identifies malware
* Connect Wordfence logs to external storage so you can access them even if Wordfence is deleted.
