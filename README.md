# 1. Containerize Your Applications:
Ensure that your front-end, backend, and database applications are properly containerized using Docker. Each should have its own Dockerfile.
# 2. Push Docker Images to Docker Hub:
Push the Docker images of your front-end, backend, and database applications to Docker Hub. Tag each image with a version or a meaningful label.
# 3. Set Up Google Cloud Project:
Create a Google Cloud account, set up a project, enable billing, and activate the Kubernetes Engine API.
# 4. Install and Configure gcloud CLI:
Install the Google Cloud SDK and authenticate using gcloud auth login.
# 5. Create a GKE Cluster:
Use the gcloud CLI to create a Kubernetes cluster on GKE. Specify the number of nodes, machine type, and other configurations.
# 6. Configure kubectl:
Configure kubectl to point to your GKE cluster:

gcloud container clusters get-credentials <cluster-name> --zone <zone>

# 7. Create StatefulSets:
Create StatefulSets for your backend application and database. StatefulSets maintain stable network identities for the pods.

Create a StatefulSet manifest (backend-statefulset.yaml):

<img width="365" alt="image" src="https://github.com/spiral99/yolo-cluster/assets/65442188/e45ec174-a6b9-48e8-afaa-9f1849863a71">

Create a StatefulSet manifest (database-statefulset.yaml):

<img width="362" alt="image" src="https://github.com/spiral99/yolo-cluster/assets/65442188/8b4dcf9b-6f92-4bc9-8e60-d829cfe1eab7">

# 8. Apply StatefulSets:
Apply the StatefulSet manifests to create the backend and database StatefulSets on your GKE cluster:

kubectl apply -f backend-statefulset.yaml
kubectl apply -f database-statefulset.yaml

# 9. Expose Services:
Create services to expose the backend and database StatefulSets.

Create a service manifest (backend-service.yaml):

<img width="364" alt="image" src="https://github.com/spiral99/yolo-cluster/assets/65442188/5c3dd0c0-e6ef-4269-965f-159581b2dee2">

Create a service manifest (database-service.yaml):

<img width="368" alt="image" src="https://github.com/spiral99/yolo-cluster/assets/65442188/f4abab14-7b8b-4a22-b952-da77bf8a4b6d">

Apply the service manifests:

kubectl apply -f backend-service.yaml
kubectl apply -f database-service.yaml

# 10. Deploy Front-End:
Deploy your React front-end application using a Deployment or StatefulSet as needed. Create a deployment manifest (frontend-deployment.yaml):

<img width="368" alt="image" src="https://github.com/spiral99/yolo-cluster/assets/65442188/834a5065-88a6-45ff-8f3d-0e4fefe6ab15">

Apply the deployment manifest:

kubectl apply -f frontend-deployment.yaml

# 11. Access the Applications:
After a moment, you can use the services' ClusterIPs to communicate between your front-end, backend, and database applications.
Remember, this is a simplified guide, and actual implementations might require additional configurations like environment variables, secret management, and database initialization. Always ensure you follow best practices for security, scalability, and maintainability.

# 12. Working site:
http://44.206.242.56:3000/

<img width="1267" alt="image" src="https://github.com/spiral99/yolo-cluster/assets/65442188/8d5b7f4f-43ec-4726-a49a-88ca702cdd71">
