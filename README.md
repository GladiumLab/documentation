Pantheon Documentation
======================

Documentation Site
------------------

Visit https://pantheon.io/docs/ for the latest release of Pantheon documentation, which is:

-   Version-controlled
-   Forkable
-   Continuously updated
-   Written in markdown
-   Generated by [Sculpin][1]

    [1]: <https://sculpin.io/>

Usage
-----

#### 0. Get the code.
Fork and clone this repository. Issue pull-requests one document at a time.

### Running Locally

#### 1. Get composer.

If you don't already have it, you can install it quickly:

~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~
curl -sS https://getcomposer.org/installer | php
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~
If you need to install it globally, 
```
mv composer.phar /usr/local/bin/composer
```
#### 2. Install dependencies:

From within the `documentation` repo, run composer install

~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~
composer install
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

That will download all your dependencies and set up sculpin.

#### 3. Start local server:

Build sculpin and run a local instance:

~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~
./vendor/bin/sculpin generate
./vendor/bin/sculpin server 
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

You can now visit your docs site at <http://localhost:8000/docs>

 

You can combine the two actions: generate the docs and start the server:

~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~
./vendor/bin/sculpin generate --server
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

 

Finally, you can tell sculpin to watch the docs directory and automatically
regenerate anything changed:

~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~
./vendor/bin/sculpin generate --server --watch
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

 

If you use --watch and see it constantly running, regenerating, drop --watch
until you identify and resolve the problem.

Images won't show up locally unless you apply these commands:
```
$ cd output_dev
$ ln -s ./ source
```

### Style Guide

Read [style-guide.md](<style-guide.md>) for our guidelines on how to write
documentation.

### Contributing

Read [CONTRIBUTING.md](<CONTRIBUTING.md>) for more details on contributing
documentation improvements.
