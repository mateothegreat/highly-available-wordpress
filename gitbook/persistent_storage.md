# Persistent Storage

This example makes use of [persistent disks](https://cloud.google.com/compute/docs/disks/), allowing the application to preserve its state across pod shutdown and start-up.

### Using the cloud shell (gcloud):
```
$ gcloud compute --project "my-test-load-balancing-project" disks create "wordpress-disk-1" --size "200" --zone "us-central1-a" --descripti
on "Persistent disk for WordPress Cluster" --type "pd-standard"

Created [https://www.googleapis.com/compute/v1/projects/my-test-load-balancing-project/zones/us-central1-a/disks/wordpress-disk-1].
NAME              ZONE           SIZE_GB  TYPE         STATUS
wordpress-disk-1  us-central1-a  200      pd-standard  READY
```


### Using the web console:
You will need to change sections and go to the Compute Engine -> Disks section:

![](https://goo.gl/2c7SAB)