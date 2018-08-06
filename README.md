# ClickCount deploy scripts

## Prerequisites

* Vagrant 2.0
* VirtualBox 5.2
* Ansible 2.4

## Initializing the environment

```
vagrant up
```

## Instructions

* Access jenkins on http://localhost:8080

* Login with admin/admin2

* Manually start the "clickcount-build" job or wait 5 minutes for the build to
  start
* The "clickcount-deploy-staging" job will run on every successful build
* Manually run the "clickcount-deploy-prod" job

## URL

* Staging: http://localhost:8081/clickCount/
* Prod: http://localhost:8082/clickCount/
