# Kubernetes MongoDB & Mongo Express Deployment – Student Instructions

## Objective

Your task is to deploy a MongoDB database and a Mongo Express web interface on Kubernetes using Minikube. You will write all the necessary YAML files yourself.
0 This exercise will help you practice planning and creating Kubernetes resources for a real-world stack.

## Requirements

You must create the following Kubernetes resources:

1. **Secret** – Store the MongoDB root username and password securely.
2. **ConfigMap** – Store the MongoDB service address for use by Mongo Express.
3. **MongoDB Deployment & Service** – Deploy MongoDB and expose it within the cluster.
4. **Mongo Express Deployment & Service** – Deploy Mongo Express and expose it for external access.

**Default MongoDB Credentials:**
- Username: `username`
- Password: `password`

## Instructions
### 1. Plan Your Resources

- Decide what information should be stored in a Secret (e.g., database credentials).
- Decide what configuration should go in a ConfigMap (e.g., database service address).
- Plan the Deployments for MongoDB and Mongo Express, including environment variables, images, and ports.
- Plan the Services to expose MongoDB internally and Mongo Express externally (for Minikube, use type: NodePort for external access).

### 2. Create the YAML Files

Write separate YAML files for each resource:

- `mongo-secret.yaml` – for the Secret.
- `mongo-configmap.yaml` – for the ConfigMap.
- `mongo.yaml` – for MongoDB Deployment and Service.
- `mongo-express.yaml` – for Mongo Express Deployment and Service.

**Do not copy code from anywhere. Write the YAML yourself!**

### 3. Apply the Resources

Use `kubectl apply -f <filename>` to create each resource in your cluster, in this order:

1. Secret
2. MongoDB Deployment & Service
3. ConfigMap
4. Mongo Express Deployment & Service

### 4. Verify the Deployment

- Check that all pods are running:  
  `kubectl get pods`
- Check that all services are created:  
  `kubectl get services`
- Access Mongo Express using the external service:
  - Find the NodePort for the Mongo Express service.
  - Run:  
    `minikube service mongo-express-service`  
    This will open the Mongo Express web interface in your browser.

### 5. Clean Up

When finished, delete all resources using:  
`kubectl delete -f <filename>` for each YAML file.

---

**Tips:**

- Use environment variables in your Deployments to pass credentials and configuration.
- Use `valueFrom` to reference Secrets and ConfigMaps in your Deployments.
- Make sure the Mongo Express Deployment can connect to the MongoDB Service using the correct address and credentials.
- For Minikube, always use `type: NodePort` for services you want to access from your browser.	

---

**Goal:**  
By the end of this exercise, you should be comfortable designing and writing Kubernetes resource files for a multi-component stack, using best practices for configuration and secrets management.