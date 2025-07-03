# Steps to remediate a hacked Wordpress site

## Collect data

Identify how and when the site was hacked:
* Check if any third party plugins and themes need updating, and if any vulnerabilities have been reported.<br>[Search plugin vulnerabilities on wordfence.com](https://www.wordfence.com/threat-intel/vulnerabilities/wordpress-plugins)
* Check for modified core files and look up suspicious filenames or code. (You can use [Sucuri](https://wordpress.org/plugins/sucuri-scanner/) to find new or modified files in core. [Wordfence](https://wordpress.org/plugins/wordfence/) was not as good for this, it did not find a test php file I placed in core.)
* Run a database scan. ([GOTMLS (https://wordpress.org/plugins/gotmls/)] has a "database injections" option.)
* Look at logs (Check email logs for suspicious emails, look at Wordfence logs if it hasn't been removed...)
* Check if the site is on Google's blocklist.

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

1. Identify the tables you want to migrate, and scan them for malware patterns.
2. Remove any suspicious or spam data.
3. Migrate tables to new install.
4. Identify how suspicious data ended up there and take steps to prevent it happening in the future.

## Post remediation

Set up regular backups with hosting service.

Set plugins to auto-update if possible.

Configure firewall, core file scan and database scan. There are a bunch of plugins that do this but none of them do all three for free. Here's the ones I use:
* Firewall: [Wordfence](https://wordpress.org/plugins/wordfence/) -- Limit login attemps and 404s (often a sign of bots scanning the website for vulnerabilities.)
* Core file scan: [Sucuri](https://wordpress.org/plugins/sucuri-scanner/)
* Database scan: [GOTMLS](https://wordpress.org/plugins/gotmls/)
