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

## Here is a sample log
   2018-02-25T14:19:42.38+1100 [RTR/8] OUT cf-nodejs-agile-oryx.cfapps.io - [2018-02-25T03:19:42.380+0000] "GET / HTTP/1.1" 200 0 5570 "-" "HTTPie/0.9.9" "10.10.66.20:62853" "10.10.148.164:61008" x_forwarded_for:"49.2.62.195, 10.10.66.20" x_forwarded_proto:"http" vcap_request_id:"f7253a59-e5ee-4996-4254-d1c9eb5f50a7" response_time:0.005217516 app_id:"8bc63051-adda-4d38-81ad-8ff2b85cb4f9" app_index:"1" x_b3_traceid:"0a75b53379081707" x_b3_spanid:"0a75b53379081707" x_b3_parentspanid:"-"
   2018-02-25T14:19:42.38+1100 [RTR/8] OUT
   2018-02-25T14:19:42.38+1100 [APP/PROC/WEB/1] OUT GET Request RCV

```

### Finally delete your application

``` bash

cf delete cf-nodejs

```


## References

-- CF Commands - http://cli.cloudfoundry.org/en-US/cf/
-- https://docs.cloudfoundry.org/buildpacks/node/node-tips.html
