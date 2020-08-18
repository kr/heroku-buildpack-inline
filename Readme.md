# Heroku Buildpack: Inline

This is a [Heroku buildpack][buildpack] for Heroku apps that
wish to build themselves.

It expects the app to provide the usual buildpack executables
in its source tree, in a directory named "bin" in the top of
the git repo; this is the same interface all other buildpacks
provide. See the [buildpack documentation][buildpack] for more
details about this interface.

Thus, an app serves as its own buildpack.

Phil Hagelberg originated this lovely idea.

## Usage

    $ find . -type f -print
    ./bin/compile
    ./bin/detect
    ./bin/release
    ./bin/run
    ./Procfile

    $ cat Procfile
    work: bin/run

    $ heroku create
    ...

    $ heroku buildpacks:add -i 1 heroku-community/inline
    ...

    $ git push heroku master
    ...

[buildpack]: http://devcenter.heroku.com/articles/buildpack
