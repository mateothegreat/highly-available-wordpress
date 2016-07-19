# Persistent Storage

This example makes use of [persistent disks](https://cloud.google.com/compute/docs/disks/), allowing the application to preserve its state across pod shutdown and start-up.

### Using the cloud shell (gcloud):
```
$ gcloud compute --project "gowoo-1358" disks create "wordpress-disk-1" --size "200" --zone "us-cen
tral1-b" --description "Persistent disk for WordPress Cluster" --type "pd-standard"
Created [https://www.googleapis.com/compute/v1/projects/gowoo-1358/zones/us-central1-b/disks/wordpress-disk-1].
NAME              ZONE           SIZE_GB  TYPE         STATUS
wordpress-disk-1  us-central1-b  200      pd-standard  READY
```
![](https://goo.gl/BqT9lO)

### Using the web console:
You will need to change sections and go to the Compute Engine -> Disks section:

![](https://goo.gl/2c7SAB)