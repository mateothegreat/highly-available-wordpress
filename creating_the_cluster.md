# Create a Container Engine cluster

The first step is to create a Container Engine cluster on which you'll run your site. The following command creates a cluster with 2 nodes:

```
$ gcloud container clusters create wppd --num-nodes 2
Creating cluster wppd...done.
Created [https://container.googleapis.com/v1/projects/container-engine-docs/zones/us-central1-b/clusters/wppd].
kubeconfig entry generated for wppd.
NAME  ZONE           MASTER_VERSION  MASTER_IP  MACHINE_TYPE   NODE_VERSION  NUM_NODES  STATUS
wppd  us-central1-b  1.2.0           x.x.x.x    n1-standard-1  1.2.0         2          RUNNING
```