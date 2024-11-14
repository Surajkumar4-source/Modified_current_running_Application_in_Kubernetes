
# Assignment: Docker & Kubernetes Deployment, Image Management, and Rollback
Objective:
<br>

1. Create a Kubernetes deployment.
2. Build a Docker image from the application.
3. Push the image to Docker Hub.
4. Modify the application running in Kubernetes by updating the image.
5. Rollback to the previous version in case of an error.


## Follow the Steps to Implement:

### Step 1: Create a Kubernetes Deployment
- First, we will create a Kubernetes deployment to run our application.

  *Create the deployment named suraj-app with a specified Docker image and 3 replicas:*
```yml
kubectl create deployment suraj-app --image=surajkumar12345/second_img --port=80 --replicas=3
```

### Step 2: Build Docker Image
- Next, we will build a Docker image from the Dockerfile of our application.

    *Build the Docker image for the application (version v2):*
```yml
sudo docker build -t surajkumar12345/second_img:v2 .
```

### Step 3: Push Docker Image to Docker Hub
- After building the Docker image, we push it to Docker Hub (or any other registry).

   *Push the image to Docker Hub with the tag v2:*
```yml
sudo docker push surajkumar12345/second_img:v2
```

### Step 4: Update the Kubernetes Deployment
- Now that our image is available in the registry, we will update the running Kubernetes deployment to use this new image.
  

   *Update the deployment suraj-app to use the new image version v3:*
```yml
kubectl set image deployment/suraj-app suraj-app-container=surajkumar12345/second_img:v3
```

### Step 5: Modify the Current Running Application
- If we want to modify the application (for example, change the application code, configurations, or environment), we need to rebuild the Docker image and update the deployment.

  *Example Scenario: Modify the Application Code*
1. Modify the code (e.g., update the app1 code in your local directory).

2. Rebuild the Docker image with the new code changes (new version v4):

```yml
sudo docker build -t surajkumar12345/second_img:v4 .
```

3. Push the updated image to Docker Hub with the new version:

```yml
sudo docker push surajkumar12345/second_img:v4
```

4. Update the deployment to use the new image version v4:

```yml
kubectl set image deployment/suraj-app suraj-app-container=surajkumar12345/second_img:v4
```

### Step 6: Check the Deployment Status
- Verify if the deployment has been successfully updated and running with the new image.

1. Check the status of the rollout:
```yml
kubectl rollout status deployment/suraj-app
```

### Step 7: Rollback to Previous Version (if error occurs)
- If there is an error with the new version (e.g., the application is not running correctly), we can rollback to the previous stable version.

1. Rollback to the previous version of the deployment:
```yml
kubectl rollout undo deployment/suraj-app
```

### Step 8: Verify the Rollback
- After rolling back, ensure that the deployment is now running with the previous stable version.

1. Check the deployment details to confirm the rollback:
```yml
kubectl describe deployment suraj-app
```

<br>

## Deliverables:
- A sequence of commands executed to deploy the application, build and push the image, modify the application, update the Kubernetes deployment, and rollback if necessary.
  
- Screenshots or logs showing the status of the deployment at different stages (initial deployment, updated image, modification, and rollback).



## Key Concepts:
- Deployment Management: You created, updated, and deleted deployments. You used image versioning to manage application updates.
- Image Versioning: You built and pushed several versions of the Docker image (v2, v3, v4) and updated the deployments accordingly.
- Modifying Running Applications: You modified the application code, rebuilt the Docker image, and updated the running pods.
- Scaling & Rollbacks: You scaled deployments and performed rollbacks to revert to previous versions when needed.


<br>
  
This assignment will help me  understand how to manage Kubernetes deployments, handle Docker image versions, modify applications in running pods, and perform rollbacks in case of issues.


