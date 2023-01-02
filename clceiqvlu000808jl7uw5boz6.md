# How to create a Deployment file for cloud run and mongo DB Atlas cluster!

## **Imports**

We will need to import the following modules to use Deployment Manager:

```yaml
imports:
- path: cloudrun.jinja
  name: cloudrun
- path: mongodbatlas.jinja
  name: mongodbatlas
```

## **Resources**

### **Cloud Run**

We will create a Cloud Run service with the following configuration:

```yaml
resources:
- type: cloudrun.jinja
  name: my-cloud-run-service
  properties:
    region: us-central1
    memory: 1Gi
    cpu: 1
    concurrency: 10
    sourceImage: gcr.io/my-project/my-image:latest
    environmentVariables:
      - name: MY_ENV_VAR
        value: my-value
```

### **MongoDB Atlas Cluster**

We will create a MongoDB Atlas cluster with the following configuration:

```yaml
- type: mongodbatlas.jinja
  name: my-atlas-cluster
  properties:
    region: us-central1
    clusterSize: 3
    clusterType: M10
    backupEnabled: true
    backupWindowStart: 21:00
    backupWindowDuration: 8
    clusterName: my-atlas-cluster
    projectId: my-project-id
    apiKeys:
      - keyName: my-api-key
        readOnly: true
```

## **Outputs**

We will output the URL of the Cloud Run service and the connection string for the MongoDB Atlas cluster:

```yaml
outputs:
- name: cloud-run-url
  value: $(ref.my-cloud-run-service.status.url)
- name: atlas-cluster-connection-string
  value: $(ref.my-atlas-cluster.connectionString)
```