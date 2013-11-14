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

```
$ st push -n
Using manifest file "stackato.yml"
Application Url: blogsite.stackato-xxxx.local
Creating Application [blogsite] as [https://api.stackato-xxxx.local -> test-org -> demo -> blogsite] ... OK
Map blogsite.stackato-xxxx.local ... OK
Uploading Application [blogsite] ... 
Checking for bad links ... 13 OK
Copying to temp space ... 12 OK
Checking for available resources ... 8773 < 64K, skip OK
Processing resources ... OK
Packing application ... OK
Uploading (4K) ... 100% OK
Push Status: OK
Starting Application [blogsite] ... 
stackato.dea_ng: [STAGING_APP] Staging application
stackato.cloud_controller: [APP_UPDATED] Updated app 'blogsite' -- {"console"=>true, "state"=>"STARTED"}
staging: -----> Downloaded app package (8.0K)
staging: Cloning into '/tmp/buildpacks/heroku-buildpack-jekyll'...
staging: -----> Installing jekyll version 1.3.0
staging:        Building native extensions.  This could take a while...
staging:        Building native extensions.  This could take a while...
staging:        Building native extensions.  This could take a while...
staging:        Building native extensions.  This could take a while...
staging:        Building native extensions.  This could take a while...
staging:        Successfully installed liquid-2.5.4
staging:        Successfully installed fast-stemmer-1.0.2
staging:        Successfully installed classifier-1.3.3
staging:        Successfully installed rb-fsevent-0.9.3
staging:        Successfully installed ffi-1.9.3
staging:        Successfully installed rb-inotify-0.9.2
staging:        Successfully installed rb-kqueue-0.2.0
staging:        Successfully installed listen-1.3.1
staging:        Successfully installed syntax-1.0.0
staging:        Successfully installed maruku-0.6.1
staging:        Successfully installed yajl-ruby-1.1.0
staging:        Successfully installed posix-spawn-0.3.6
staging:        Successfully installed pygments.rb-0.5.4
staging:        Successfully installed highline-1.6.20
staging:        Successfully installed commander-4.1.5
staging:        Successfully installed safe_yaml-0.9.7
staging:        Successfully installed colorator-0.1
staging:        Successfully installed redcarpet-2.3.0
staging:        Successfully installed jekyll-1.3.0
staging:        19 gems installed
staging: -----> Setting environment variables
staging: -----> Compiling Jekyll site
staging: Configuration file: none
staging:                    Source: /tmp/staged
staging:               Destination: /tmp/staged/_site
staging:              Generating... done.
staging: -----> Uploading droplet (9.3M)
stackato.dea_ng: [STAGED_APP] Completed staging application
stackato.dea_ng.0: [SPAWNING_APP] Spawning app web process: env GEM_HOME=./.gems ./.gems/bin/jekyll serve --port $PORT
app.0[stdout]: Configuration file: /home/stackato/app/_config.yml
app.0[stdout]:             Source: /home/stackato/app
app.0[stdout]: 
app.0[stdout]:        Destination: /home/stackato/app/_site
app.0[stdout]: 
app.0[stdout]:       Generating... 
app.0[stdout]: done.
app.0[stdout]:     Server address: http://0.0.0.0:49073
app.0[stdout]:   Server running... press ctrl-c to stop.
OK
http://blogsite.stackato-xxxx.local/ deployed
```
