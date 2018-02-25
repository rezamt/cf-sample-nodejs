# Node.js Sample Application

### Deploy Application to CloudFoundry

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

## References

-- https://docs.cloudfoundry.org/buildpacks/node/node-tips.html
