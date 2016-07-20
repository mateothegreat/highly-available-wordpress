{% include "./includes/header.md" %}

![](../images/gcp-container-engine.png)
## Create the Service

```
$ kubectl create -f https://raw.githubusercontent.com/mateothegreat/highly-available-wordpress/master/src/wordpress-service.yaml

service "wpfrontend" created
```