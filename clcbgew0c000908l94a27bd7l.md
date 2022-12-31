# Write Your First Deployment Manager File for Storage in GCP

## **Introduction**

This Deployment Manager file will create a storage bucket in the Google Cloud Platform (GCP). The bucket will be used to store data, such as files and images, for a project or application.

## **Resources**

The following resources will be created as part of this deployment:

* A storage bucket
    
* An IAM policy to grant access to the bucket
    

## **Variables**

The following variables will be used in this deployment:

* `project_id`: The ID of the GCP project in which the bucket will be created.
    
* `bucket_name`: The name of the storage bucket.
    
* `location`: The location of the bucket. This will determine the geographic location of the bucket and the location of the data stored in it.
    
* `iam_user`: The email address of the IAM user who will be granted access to the bucket.
    

## **Deployment**

To deploy this configuration, run the following command:

```bash
gcloud deployment-manager deployments create storage-bucket --config storage-bucket.yaml
```

## **Configuration**

This is the configuration file for the deployment:

```yaml
resources:
  - name: storage-bucket
    type: storage.v1.bucket
    properties:
      name: "${bucket_name}"
      location: "${location}"
  - name: iam-policy
    type: iam.v1.policy
    properties:
      policy:
        bindings:
        - role: roles/storage.objectAdmin
          members:
          - user:${iam_user}
      resource: "projects/${project_id}/buckets/${bucket_name}"
```

## **Notes**

* The IAM policy grants the specified user the `storage.objectAdmin` the role, which allows them to manage the objects in the bucket.
    
* The location of the bucket should be chosen based on the location of the data and the users who will access it. Choosing a location closer to these users can improve performance.