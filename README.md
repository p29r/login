# login
LogIn module  


This action builds docker image from the Dockerfile in the root of the repository, Pushes it to Google Container Registry and then updates the specified deployment running in the GKE(Google Kubernetes Engine)

## Inputs

### `service_account`

**Required** Service account from GCP IAM, should have access to GCR and GKE. How to generate service account : 
1. Go to IAM , select service account
2. Name it, give required premissions and click create key and select JSON. It will download a json file
3. Run this : cat downloaded_file.json | base64 | tr -d '\n'
4. Take the output from step 3, and save it in a secret (recommended). In example below I am saving it as GCLOUD_AUTH. 

### `zone`

**Required** Zone in which GKE cluster is running.

### `project_id`

**Required** Project id of the GCP Project.

### `resgistry`

**Required** Registry host, specifies location where you want to store images, possible values are : gcr.io/us.gcr.io/eu.gcr.io/asia.gcr.io. Default `"gcr.io"`.

### `image_name`

**Required** Name of the which that will be pushed to GCR.

### `cluster`

**Required** Name of GKE cluster.

### `namespace`

**Required** Namespace in which deployment is deployed and needs to be updated. Default `"default"`.

### `deployment`

**Required** Name of GKE deployment.

### `container`

**Required** Name of container inside the pod, which needs to be updated.