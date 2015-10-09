# Discord Development Guide

The first step to 

## Install the Pre-Requisites

We're assuming you're going to deploy your development environment on Ubuntu.  If this isn't the case, you'll have to figure out what packages replace these for your distribution.

* postgres
* libpq-dev
* haskell-platform

After you get these installed, you will want to run

    cabal update && cabal install yesod-bin

Getting the `yesod` executables compiled will take a few minutes.  Once that is taken care of, you will have to build a sandbox in your discord directory.

    git clone https://github.com/PoissonLabs/discord
    cd discord
    cabal sandbox init
    cabal install


## Configure postgres

You can do these while `yesod` and `discord` compile.  Run the following commands to configure postgres.

    sudo -i postgres
    createuser --pwprompt --no-createrole --no-superuser discord
    createdb discord

The createuser command will ask you to enter a password, twice.  For a development machine, enter `discord` both times.  We recommend entering a different password for production.  Your `discord` instance will be able to access the database if you set environment variables in your run-script.  More on that later.
