{% include "./includes/header.md" %}

![](../images/gcp-compute-engine-clusters.png)
## Create the Service

```
$ kubectl create -f https://raw.githubusercontent.com/mateothegreat/highly-available-wordpress/master/src/wordpress-service.yaml

service "wpfrontend" created
```