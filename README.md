# MongoDB and Mongo Express Deployment with Ingress

This project demonstrates how to deploy MongoDB and Mongo Express using Kubernetes with Ingress. It includes all necessary Kubernetes manifests and commands for setup, monitoring, debugging, and external access.

---

## **Commands Overview**

### **1. Apply Kubernetes Manifests**
Apply the manifests in the following order:

```bash
kubectl apply -f mongo-secret.yaml
kubectl apply -f mongo.yaml
kubectl apply -f mongo-configmap.yaml
kubectl apply -f mongo-express.yaml
```

### **2. Monitor the Deployment**
Use the following commands to monitor the Pods, Services, and Secrets:

#### **Get Pods**
```bash
kubectl get pod
kubectl get pod --watch
kubectl get pod -o wide
```

#### **Get Services**
```bash
kubectl get service
```

#### **Get Secrets**
```bash
kubectl get secret
```

#### **Get All Resources (Filtered by MongoDB)**
```bash
kubectl get all | grep mongodb
```

---

### **3. Debugging Commands**
Use these commands to troubleshoot issues with the deployment:

#### **Describe the MongoDB Pod**
```bash
kubectl describe pod mongodb-deployment-xxxxxx
```

#### **Describe the MongoDB Service**
```bash
kubectl describe service mongodb-service
```

#### **View Logs from Mongo Express**
```bash
kubectl logs mongo-express-xxxxxx
```

---

### **4. Access the External Service (Minikube)**

To access the Mongo Express service externally in a Minikube environment, use the following command:

```bash
minikube service mongo-express-service
```

This will output a URL. Open the URL in your browser to access Mongo Express.

---

## **Project Structure**

- **`mongo-secret.yaml`**: Contains the MongoDB username and password stored as Kubernetes secrets.
- **`mongo.yaml`**: Deploys MongoDB as a Pod and Service.
- **`mongo-configmap.yaml`**: Stores configuration for MongoDB such as database URL.
- **`mongo-express.yaml`**: Deploys Mongo Express as a Pod and Service for a web-based MongoDB interface.

---

## **Usage**
1. Apply all manifests using the commands in the correct order.
2. Monitor and debug the deployment using the provided commands.
3. Access Mongo Express using the Minikube service URL.

---

### **Notes**
- Ensure Minikube is running before deploying the manifests.
- Replace `xxxxxx` with the actual Pod name from the `kubectl get pod` output.
- For production environments, consider using a LoadBalancer or Ingress Controller for external access instead of Minikube.

