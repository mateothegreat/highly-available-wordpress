
[](https://cloud.google.com/container-engine/)![](../images/gcp-container-engine.png)

---
<img src="../images/docker-kubernetes2.png" style=" float: right; margin: 20px;"> [Google Container Engine](https://cloud.google.com/container-engine/) is a powerful cluster manager and orchestration system for running your Docker containers. Container Engine schedules your containers into the cluster and manages them automatically based on requirements you define (such as CPU and memory). It's built on the open source [Kubernetes](http://kubernetes.io/) system, giving you the flexibility to take advantage of on-premises, hybrid, or public cloud infrastructure.

[](https://cloud.google.com/container-engine/)We'll use the official [WordPress](https://registry.hub.docker.com/_/wordpress/) Docker image for this installation. The WordPress docker image includes an Apache server. You can use any docker container you want however.

#### Before you begin

[Follow the directions](https://cloud.google.com/container-engine/docs/before-you-begin) to:

* Enable the API in Cloud Console.
* Install the `gcloud` and `kubectl` command line interfaces.
* Set your default project and Compute Engine zone.

#### Setup Templates
We will be using the template files below to set things up. Notice that there are some variables that need to be updated with your information.

Templates:
* `wordpress.yaml`: The WordPress **pod** configuration file. [[Download](https://github.com/mateothegreat/highly-available-wordpress/blob/master/src/wordpress.yaml)]
* `wordpress-service.yaml`: The WordPress **service** configuration file. [[Download](https://github.com/mateothegreat/highly-available-wordpress/blob/master/src/wordpress-service.yaml)]

#### Creating Resources
You can apply your templates with the gcloud console to deploy your resources:
```
gcloud container --project "my-test-load-balancing-project" clusters create "cluster-1" --zone "us-central1-a" \
  --machine-type "n1-standard-1" \
  --scope "https://www.googleapis.com/auth/compute","https://www.googleapis.com/auth/devstorage.read_only","https://www.googleapis.com/auth/logging.write","https://www.googleapis.com/auth/monitoring","https://www.googleapis.com/auth/servicecontrol","https://www.googleapis.com/auth/service.management" \
  --num-nodes "2" --network "network-1" --enable-cloud-logging --enable-cloud-monitoring

Creating cluster cluster-1...done.
Created [https://container.googleapis.com/v1/projects/my-test-load-balancing-project/zones/us-central1-a/clusters/cluster-1].

kubeconfig entry generated for cluster-1.
NAME       ZONE           MASTER_VERSION  MASTER_IP        MACHINE_TYPE   NODE_VERSION  NUM_NODES  STATUS
cluster-1  us-central1-a  1.3.2           104.198.224.238  n1-standard-1  1.3.2         2          RUNNING
```