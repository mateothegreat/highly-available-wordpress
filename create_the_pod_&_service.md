# Create the WordPress pod


The wordpress.yaml file defines a pod with a single wordpress container, and mounts a volume on the container using the wordpress-disk persistent disk that you created earlier.

We need to setup kubernetes:
```
$ gcloud container clusters get-credentials wordpress-cluster-1 --zone us-central1-b

Fetching cluster endpoint and auth data.
kubeconfig entry generated for wordpress-cluster-1.
```

#### Example wordpress.yaml
```
apiVersion: v1
kind: Pod
metadata:
  name: wordpress
  labels:
    name: wordpress
spec:
  containers:
    - image: wordpress
      name: wordpress
      env:
        - name: WORDPRESS_DB_HOST
          value: <hostname from sql server creation>
        - name: WORDPRESS_DB_USER
          value: <username from sql server creation>
        - name: WORDPRESS_DB_NAME
          value: <database name from sql server creation>
        - name: WORDPRESS_DB_PASSWORD
          value: yourpassword
      ports:
        - containerPort: 80
          name: wordpress
      volumeMounts:
          # Name must match the volume name below.
        - name: wordpress-persistent-storage
          # Mount path within the container.
          mountPath: /var/www/html
  volumes:
    - name: wordpress-persistent-storage
      gcePersistentDisk:
        # This GCE persistent disk must already exist.
        pdName: wordpress-disk-1
        fsType: ext4
```

### Creating the Pod

```
$ kubectl create -f https://raw.githubusercontent.com/mateothegreat/highly-available-wordpress/master/src/wordpress.yaml

pod "wordpress" created
```

Check to see if the pod is running (It may take a few minutes to change from Pending to Running):

```
$ kubectl get pod wordpress
NAME        READY     STATUS    RESTARTS   AGE
wordpress   1/1       Running   0          28s
```