# Jekyll Buildpack

The Jekyll Buildpack will look for a file named `_config.yml` in the app root and run Jekyll to create and serve the site.

This variant is designed to work on Stackato:

http://www.activestate.com/stackato

## Usage

Specify this buildpack in the `buildpack` key in a top-level `stackato.yml` file. For example: 

```
name: yoursite
mem: 128M
buildpack: git://github.com/ActiveState/heroku-buildpack-jekyll.git
```

Push the application to the target with `stackato push -n`.
