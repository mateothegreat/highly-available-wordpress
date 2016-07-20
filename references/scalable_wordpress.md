![](../images/chrome_2016-07-19_22-54-12.png)

---

# Scalable WordPress


## Pre-requisites
Set these resources up before the next section:

* (1) [Google SQL Server Instance](storage/persistent_storage.md)
* (1) [Persistent Hard Drive](storage/persistent_storage.md)
* (1) [Container Engine Cluster](containers/create_the_cluster.md)

## Service Setup

* Grap the templates for pod and service from the [Container Engine](containers/the_container.md) page (clone the repo and edit or simply use a pastebin if you do not have any tools).
* Update both templates and replace the variables with your new IP for the database, load balancer, etc.
* With the updated pod and service configs we can spin the service up and have something actually running on the containers started from the engine cluster:
   * [Creating a Service](containers/create_the_service.md)
   * [Creating a "Pod"](containers/create_the_pod.md)