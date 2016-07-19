# Persistent Storage

This example makes use of [persistent disks](https://cloud.google.com/compute/docs/disks/), allowing the application to preserve its state across pod shutdown and start-up.

```
$ gcloud compute disks create --size 200GB wordpress-disk

    Created [https://www.googleapis.com/compute/v1/projects/container-engine-doc-test/zones/us-central1-b/disks/wordpress-disk].
    NAME           ZONE          SIZE_GB TYPE        STATUS
    wordpress-disk us-central1-b 200     pd-standard READY
```