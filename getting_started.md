# Getting Started

#### Set the default project:
```sh
gcloud config set project my-test-load-balancing-project```

#### Set the default zone:
```sh
gcloud config set compute/zone asia-east1-a 
```

#### Set the default container cluster:
```sh
gcloud config set container/cluster cluster-1
```

#### Checking out the load balancer:
```sh
[root@instance-1 ha-service]# gcloud compute forwarding-rules describe test-lb-fr --region asia-east1                                                                  
IPAddress: 104.155.231.234
IPProtocol: TCP
creationTimestamp: '2016-07-22T18:41:32.195-07:00'
description: ''
id: '3692223772804216227'
kind: compute#forwardingRule
name: test-lb-fr
portRange: 80-80
region: https://www.googleapis.com/compute/v1/projects/my-test-load-balancing-project/regions/asia-east1
selfLink: https://www.googleapis.com/compute/v1/projects/my-test-load-balancing-project/regions/asia-east1/forwardingRules/test-lb-fr
target: https://www.googleapis.com/compute/v1/projects/my-test-load-balancing-project/regions/asia-east1/targetPools/test-lb-tp
```