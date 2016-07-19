# Symfony Box

A ready LAMP environment with [Symfony2](https://symfony.com) installed, based on [Scotch Box](https://github.com/scotch-io/scotch-box).

Symfony Box...

- Sets up a basic LAMP stack
- Updates Composer
- Installs Symfony Standard Edition
- Initializes a git repo

# Requirements

This should run just fine on any system supported by VirtualBox and Vagrant, including Linux, macOS and Windows.

# Prerequisites

- VirtualBox
- Vagrant
- An idea for an app

# Usage

Recommended:

1. Create a directory for your new project (eg. `~/Documents/my-symfony-project`)
2. Download `Vagrantfile` and place it in that directory.
3. Run `vagrant up`.
4. Open your web browser to https://192.168.22.22. You may also set a hostname for this IP for easier access.

Like the original Scotch Box, you can also clone this repo and run the command, but I find the file method more portable.

# What's inside the box?

Everything that Scotch Box contains (PHP, MySQL, Git, etc.), with the following provisioning commands to install and set up Symfony the right way:

    cd /var/www
    composer self-update
    composer create-project symfony/framework-standard-edition symfony-box "2.*"
    mv symfony-box/* .
    mv symfony-box/.gitignore .
    rm -rf symfony-box
    printf "\n/*.md\n/LICENSE\n/composer.json\n/.vagrant\n" >> .gitignore
    git init
    sudo sed -i s,/var/www/public,/var/www/web,g /etc/apache2/sites-available/000-default.conf
    sudo sed -i s,/var/www/public,/var/www/web,g /etc/apache2/sites-available/scotchbox.local.conf
    sudo service apache2 restart

# Contributions

Fork it, improve it, send a PR!

# Credits

Nick, for the original [Scotch Box](https://github.com/scotch-io/scotch-box).
