# Kubernetes Fundamentals

## 1. Minikube Setup

```bash
brew install minikube kubectl
minikube start --driver=docker
minikube status
kubectl cluster-info
kubectl get nodes
kubectl get pods -A
```

## 2. Basic Kubernetes Objects

```bash
kubectl create deployment hello-k8s --image=nginx:stable-alpine
kubectl get deployments
kubectl get pods
kubectl describe deployment hello-k8s
kubectl expose deployment hello-k8s --type=NodePort --port=80
minikube service hello-k8s
kubectl scale deployment hello-k8s --replicas=3
kubectl set image deployment/hello-k8s hello-k8s=nginx:1.27-alpine
kubectl rollout status deployment/hello-k8s
kubectl logs deployment/hello-k8s
kubectl get services
kubectl get all
```

## 3. Cleanup

```bash
kubectl delete service hello-k8s
kubectl delete deployment hello-k8s
minikube stop
```

## 4. Kubernetes Architecture Notes

- **Control Plane:** Manages the cluster and makes scheduling and state-management decisions.
- **API Server:** Entry point for Kubernetes API requests.
- **etcd:** Stores cluster configuration and state.
- **Scheduler:** Selects suitable worker nodes for Pods.
- **Controller Manager:** Runs controllers that maintain the desired state.
- **Worker Node:** Runs application workloads.
- **Kubelet:** Ensures Pods are running on its node.
- **Container Runtime:** Runs containers.
- **Kube-proxy:** Implements Service networking rules when used by the cluster networking setup.
- **Pod:** Smallest deployable Kubernetes unit.
- **Deployment:** Manages application replicas and updates.
- **Service:** Provides a stable network endpoint for accessing Pods.

## 5. Screenshots

Add screenshots of the actual command outputs for:

1. Minikube installation and cluster status.
2. `kubectl get nodes` and `kubectl get pods -A`.
3. Deployment and Pod creation.
4. Application opened in the browser.
5. Scaling to three replicas.
6. Successful rolling update.

## 6. Resources

- [Kubernetes Basics Tutorial](https://kubernetes.io/docs/tutorials/kubernetes-basics/)
- [Minikube Installation Guide](https://minikube.sigs.k8s.io/docs/start/)
- [Kubernetes Architecture](https://kubernetes.io/docs/concepts/architecture/)
- [Kubernetes GitHub Repository](https://github.com/Nency-kRavaliya/Kubernetes)
