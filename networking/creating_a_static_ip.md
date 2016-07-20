{% include "./includes/header.md" %}


![](../images/gcp-networking-externalip.png)
## Creating a Static IP


```
$ gcloud compute --project "my-test-load-balancing-project" addresses create "project-public-ip" --global
Created [https://www.googleapis.com/compute/v1/projects/my-test-load-balancing-project/global/addresses/project-public-ip].
---
address: 107.178.244.68
creationTimestamp: '2016-07-19T09:37:25.141-07:00'
description: ''
id: '6710400061679069610'
kind: compute#address
name: project-public-ip
selfLink: https://www.googleapis.com/compute/v1/projects/my-test-load-balancing-project/global/addresses/project-public-ip
status: RESERVED
```

## Firewall Rules

By default we've locked down access from the outside world into our new network. We need to open up port 80 and 443 for web traffic. This will only apply to the loadbalancer -- we do not want to have the individual container instances themselves be publically accessible.

#### HTTP & HTTPS
```
$ gcloud compute --project "my-test-load-balancing-project" firewall-rules create "allow-http-to-loadbalancer" --allow tcp:80 --network "ne
twork-1" --source-ranges "0.0.0.0/0"
Created

[https://www.googleapis.com/compute/v1/projects/my-test-load-balancing-project/global/firewalls/allow-http-to-loadbalancer].
NAME                        NETWORK    SRC_RANGES  RULES   SRC_TAGS  TARGET_TAGS
allow-http-to-loadbalancer  network-1  0.0.0.0/0   tcp:80

$ gcloud compute --project "my-test-load-balancing-project" firewall-rules create "allow-https-to-loadbalancer" --allow tcp:443 --network "
network-1" --source-ranges "0.0.0.0/0"

Created [https://www.googleapis.com/compute/v1/projects/my-test-load-balancing-project/global/firewalls/allow-https-to-loadbalancer].
NAME                         NETWORK    SRC_RANGES  RULES    SRC_TAGS  TARGET_TAGS
allow-https-to-loadbalancer  network-1  0.0.0.0/0   tcp:443
```

#### Monitoring Checks
https://cloud.google.com/compute/docs/load-balancing/health-checks

```
$ gcloud compute --project "my-test-load-balancing-project" firewall-rules create "allow-http-healthcheck" --allow tcp:80 --network "networ
k-1" --source-ranges "130.211.0.0/22"

Created [https://www.googleapis.com/compute/v1/projects/my-test-load-balancing-project/global/firewalls/allow-http-healthcheck].
NAME                    NETWORK    SRC_RANGES      RULES   SRC_TAGS  TARGET_TAGS
allow-http-healthcheck  network-1  130.211.0.0/22  tcp:80

$ gcloud compute --project "my-test-load-balancing-project" firewall-rules create "allow-https-healthcheck" --allow tcp:443 --network "netw
ork-1" --source-ranges "130.211.0.0/22"

Created [https://www.googleapis.com/compute/v1/projects/my-test-load-balancing-project/global/firewalls/allow-https-healthcheck].
NAME                     NETWORK    SRC_RANGES      RULES    SRC_TAGS  TARGET_TAGS
allow-https-healthcheck  network-1  130.211.0.0/22  tcp:443

```
