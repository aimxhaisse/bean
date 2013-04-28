BEAN
====

A template to build websites in go.

How to
------

Simply fork this project, and build your website upon it.

What it contains
----------------

* a config file for basic settings
* a default template with bootstrap
* a daemonizer to run your website in background (supports chroot)
* examples of configuration files for your web server

Quick start
-----------

    git clone github.com:aimxhaisse/bean
    cd bean
    ./all.bash build
    ./all.bash start

    # browse http://localhost:8080

Real start
----------

This could be automated but you plan to extend this, so I don't want
to add any sort of magic there.

    # replace myproject by your project name in the following lines

    # clone the project
    git clone github.com:aimxhaisse/bean myproject
    cd myproject

    # rename sources/configs yo your project's name

    # I ensure it's safe with a fresh clone
    # sed.

    # edit the variables at the top of all.bash
    $EDITOR all.bash

    # optionally edit the configuration of your website
    $EDITOR root/myproject.json

    ./all.bash build
    ./all.bash start
    ./all.bash status

    # if this is ok, commit and start to play
    git commit -am "Having setup myproject from github.com:aimxhaisse/bean"

Structure
---------

* all.bash is a shell script to manage your website (build, start, stop, ...)
* daemonizer/ contains sources for the daemonizer
* root/ contains dynamic files such as the pid
* root/www/static contains files that are served statically (css, js, images)
* root/www/static contains template files for your pages

Security
--------

It is possible to run your website chrooted (the process won't be able
to leave its directory). For this you need to set CHROOT to "yes" in
all.bash. Also, your code must not rely on absolute paths, use paths
relative to the deployment directory.
