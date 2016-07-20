{% include "./includes/header.md" %}

## Cleanup


#### Delete the services

`$ kubectl delete service wpfrontend`

#### Delete the pods:

`$ kubectl delete pod wordpress`

#### Delete your cluster:

`$ gcloud container clusters delete wppd`

#### Delete the disks:

`$ gcloud compute disks delete mysql-disk wordpress-disk`