# The Container

We'll use the official [WordPress](https://registry.hub.docker.com/_/wordpress/) Docker image for this installation. 
The WordPress docker image includes an Apache server.

### Before you begin

[Follow the directions](https://cloud.google.com/container-engine/docs/before-you-begin) to:

* Enable the API.
* Install the `gcloud` and `kubectl` command line interfaces.
* Set your default project and Compute Engine zone.

We will be editing the following configuration files:

* `wordpress.yaml`: The WordPress pod configuration file.
* `wordpress-service.yaml`: The WordPress service configuration file.
