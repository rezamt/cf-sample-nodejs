# Node.js Sample Application

### Deploy Application to CloudFoundry

Make sure your CF manifest.yml has all information about your app. Here is a sample.

```
---
applications:
- name: cf-nodejs    <-- App name
  memory: 512M       <-- Container Memory size to run the app
  instances: 2       <-- number of instances (nodes)
  random-route: true <-- Create a random route ? yes

```

Then run the following commands

``` bash

# cf target -o "YOUR - ORG - NAME" -s "YOUR - ENV - NAME"

cf create-org ninja

cf create-space test

cf target -o "ninja" -s "test"

cf push

```

### Scaling out your application

``` bash

cf scale cf-nodejs -i 2

```

### List your organization / stage applications

``` bash

cf apps

```

### Getting info about your app already deployed

``` bash

cf app cf-nodejs


Showing health and status for app cf-nodejs in org ninja / space test as me@example.com...

name:              cf-nodejs
requested state:   started
instances:         2/2
usage:             512M x 2 instances
routes:            cf-nodejs-balanced-bear.cfapps.io
last uploaded:     Sun 25 Feb 12:48:30 AEDT 2018
stack:             cflinuxfs2
buildpack:         nodejs

     state     since                  cpu    memory          disk          details
#0   running   2018-02-25T03:09:39Z   0.0%   43.4M of 512M   63.3M of 1G
#1   running   2018-02-25T03:09:38Z   0.0%   43.4M of 512M   63.3M of 1G
```

### Stop / Start your Application

``` bash

cf start cf-nodejs
cf stop cf-nodejs

```

### Accessing your application logs

``` bash

cf logs cf-nodejs

```

### Finally delete your application

``` bash

cf delete cf-nodejs

```


## References

-- https://docs.cloudfoundry.org/buildpacks/node/node-tips.html
