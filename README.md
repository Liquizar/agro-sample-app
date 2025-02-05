# 🚀 NGINX Sample Application

This repository contains a simple NGINX deployment to test ArgoCD and Backstage integration on Kubernetes.

---

## 📦 Project Structure

```
.
├── k8s
│   ├── deployment.yaml
│   ├── service.yaml
│   └── kustomization.yaml
├── catalog-info.yaml
└── README.md
```

- **`deployment.yaml`**: Defines the NGINX Deployment with 2 replicas.  
- **`service.yaml`**: Exposes NGINX using a LoadBalancer service.  
- **`kustomization.yaml`**: Manages Kubernetes manifests using Kustomize.  
- **`catalog-info.yaml`**: Registers the application in Backstage.  

---

## 🚀 Deployment with ArgoCD

1. **Add Application in ArgoCD UI:**  
   - **Application Name:** `nginx-sample`  
   - **Repository URL:** `https://github.com/Liquizar/argo-sample-app.git`  
   - **Path:** `k8s`  
   - **Namespace:** `default`  
   - **Sync Policy:** Manual or Automatic  

2. **Sync the Application:**  
   - Click **"Sync"** in the ArgoCD dashboard.  

3. **Verify Deployment:**  
   ```bash
   kubectl get pods -l app=nginx
   kubectl get svc nginx-service
   ```

4. **Access the Application:**  
   - Get the external IP:  
     ```bash
     kubectl get svc nginx-service -o wide
     ```  
   - Visit `http://<external-ip>` to see the NGINX welcome page.  

---

## 📋 Backstage Integration

1. **Register the Component:**  
   - Go to Backstage → **"Create" → "Register an existing component"**.  
   - Enter the URL:  
     ```
     https://github.com/Lquizar/argo-sample-app/blob/main/catalog-info.yaml
     ```  
   - Click **"Analyze" → "Import"**.  

2. **Verify in Backstage:**  
   - Navigate to **"Catalog"** → Click on **"nginx-sample-app"**.  
   - View ArgoCD deployment status.  

---

## ⚙️ Tech Stack

- **Kubernetes** (K3s)  
- **ArgoCD** for GitOps deployment  
- **Backstage** for developer portal  
- **NGINX** as a sample application  

---

## 🤝 Contributing

1. Fork the repository.  
2. Create a new branch: `git checkout -b feature-name`  
3. Commit your changes: `git commit -m 'Add new feature'`  
4. Push to the branch: `git push origin feature-name`  
5. Create a Pull Request.  

---

## 🙋‍♂️ Support

If you face any issues, feel free to open an [issue](https://github.com/Liquizar/argo-sample-app/issues).

---

Happy Deploying 🚀
```
