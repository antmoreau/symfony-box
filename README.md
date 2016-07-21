# Symfony Box

A ready LAMP environment with [Symfony2](https://symfony.com) installed, based on [Scotch Box](https://github.com/scotch-io/scotch-box).

Symfony Box...

- Sets up a basic LAMP stack
- Updates Composer
- Installs Symfony Standard Edition
- Initializes a git repo

# Requirements

This should run just fine on any system supported by VirtualBox and Vagrant, including Linux,
macOS and Windows.

# Prerequisites

- VirtualBox
- Vagrant
- An idea for an app

# Usage

Recommended:

1. Create a directory for your new project (eg. `~/Documents/my-symfony-project`)
2. Download `Vagrantfile` and place it in that directory.
3. Run `vagrant up`.
4. Open your web browser to https://192.168.22.22. You may also set a hostname for this IP
5. for easier access.

Like the original Scotch Box, you can also clone this repo and run the command, but I find
the file method more portable.

# What's inside the box?

Everything that Scotch Box contains (PHP, MySQL, Git, etc.), with the following provisioning
commands to install and set up Symfony the right way:

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

# A box for anything

The crux of this box is the Composer command used to install the Symfony Standard Edition.
You can easily edit `Vagrantfile` to change the version to 3.x or to change it to the core
Symfony framework (`symfony/symfony`), a different framework (`laravel/laravel`) or something
else entirely (`guzzlehttp/guzzle` or `phpunit/phpunit`).

# Contributions

Fork it, improve it, send a PR!

# Credits

Nick, for the original [Scotch Box](https://github.com/scotch-io/scotch-box).

# License

    The MIT License (MIT)
    
    Copyright (c) 2016 Aalaap Ghag
    
    Permission is hereby granted, free of charge, to any person obtaining a copy
    of this software and associated documentation files (the "Software"), to deal
    in the Software without restriction, including without limitation the rights
    to use, copy, modify, merge, publish, distribute, sublicense, and/or sell
    copies of the Software, and to permit persons to whom the Software is
    furnished to do so, subject to the following conditions:
    
    The above copyright notice and this permission notice shall be included in all
    copies or substantial portions of the Software.
    
    THE SOFTWARE IS PROVIDED "AS IS", WITHOUT WARRANTY OF ANY KIND, EXPRESS OR
    IMPLIED, INCLUDING BUT NOT LIMITED TO THE WARRANTIES OF MERCHANTABILITY,
    FITNESS FOR A PARTICULAR PURPOSE AND NONINFRINGEMENT. IN NO EVENT SHALL THE
    AUTHORS OR COPYRIGHT HOLDERS BE LIABLE FOR ANY CLAIM, DAMAGES OR OTHER
    LIABILITY, WHETHER IN AN ACTION OF CONTRACT, TORT OR OTHERWISE, ARISING FROM,
    OUT OF OR IN CONNECTION WITH THE SOFTWARE OR THE USE OR OTHER DEALINGS IN THE
    SOFTWARE.
