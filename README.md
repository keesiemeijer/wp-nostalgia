# WP Nostalgia

VVV auto site setup script to install older versions of WordPress without errors.

Most of the earlier versions of WordPress are not compatible with PHP 5.3 or higher and produce (fatal) PHP errors and all kinds of notices if you try to install. Before you know it the famous 5-minute install goes on for hours. And all you wanted to do is reunite with the 2.0 dashboard from when you first started developing (or blogging). Which was super slick compared to version 1.5-strayhorn that came before it. That's right 1.5-strayhorn! Now who doesn't want to check that out (without the errors and notices). This script gives you back the famous 5-Minute Install for [all versions of WordPress](https://wordpress.org/download/release-archive/)!

### To get started:
1. Setup [Varying Vagrant Vagrants](https://github.com/Varying-Vagrant-Vagrants/VVV) (If you don't already have it)
2. Clone this repo into the www directory of your Vagrant (`www/wp-nostalgia`)
3. If your Vagrant is running, from the Vagrant directory run `vagrant halt`
4. Followed by `vagrant up --provision`. 

You can now visit [http://wp-nostalgia.dev/readme.html](http://wp-nostalgia.dev/readme.html).
By default it has installed the very first version `0.71-gold`.

Note: If you don't have the vagrant plugin `vagrant-hostsupdater` installed you'll need to add the domain to your `hosts` file manually before you can visit [http://wp-nostalgia.dev/](http://wp-nostalgia.dev/).

### After provisioning
* (WP < 3.5.2)  Go to wp-nostalgia.dev/readme.html and follow the install instructions
* (WP >= 3.5.2) Go to wp-nostalgia.dev/wp-admin and log in with: Username: admin, Password: password

All versions higher than 3.5.2 are installed normally with [WP-CLI](http://wp-cli.org/).  
For lower versions the `wp-config.php` file is created with the right database credentials but you still have to finish the install at `wp-nostalgia.dev/readme.html`

### Usage 
This script can be used as a standalone script if you already have wp-nostalgia.dev up and running.

Example to install WordPress 2.2. First SSH into the running Vagrant machine with `vagrant ssh`

```php
cd /srv/www/wp-nostalgia
bash vvv-init.sh 2.2
```

### Notice!

* The database and directory for the WordPress install are deleted prior to installing.
* This script fixes (fatal) errors for earlier versions (WP < 2.0) by hacking core files.
* This script hides errors by setting error_reporting off in wp-config.php (WP < 3.5.2) and wp-settings.php (WP < 3.0.0)

### Database Credentials
DB Name: wp-nostalgia  
DB User: wp  

### License   
License: GPL-2.0+

### Variables
Variables you can set in the vvv-init.sh file.

```bash
# Domain name
# Note: If edited, you'll need to edit it in the vvv-hosts and the vvv-nginx.conf files as well.
readonly HOME_URL="wp-nostalgia.dev"


# WordPress version to be installed. Default: "0.71-gold"
# See the release archive: https://wordpress.org/download/release-archive/
# 
# Use a version number or "latest"
WP_VERSION="0.71-gold"

# Remove errors. Default true
readonly REMOVE_ERRORS=true
```