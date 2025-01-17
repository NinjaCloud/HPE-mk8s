## Prometheus

Add stable Helm chart repository to your Helm client
```
sudo microk8s helm repo add "stable" "https://charts.helm.sh/stable"
```
Add the Prometheus Community Helm chart repository, which contains charts for Prometheus and other related tools.
```
sudo microk8s helm repo add "prometheus-community" "https://prometheus-community.github.io/helm-charts"
```
List all Helm repositories that have been added to your Helm client. You should see both the stable and prometheus-community repositories listed
```
sudo microk8s helm repo ls
``` 
Install the kube-prometheus-stack chart from the prometheus-community repository. This chart includes Prometheus, Grafana, and other monitoring tools.
```
sudo microk8s helm install kube-prometheus-stack prometheus-community/kube-prometheus-stack 
``` 
List all Helm releases. You should see the kube-prometheus-stack listed as a deployed release.
```
sudo microk8s helm ls
``` 
List all pods in all namespaces, allowing you to verify that the Prometheus and Grafana pods are running.
```
sudo microk8s kubectl get po -A
``` 
LIst all services in the default namespace. You can see the services created by the kube-prometheus-stack
```
sudo microk8s kubectl get svc 
``` 
Open the Prometheus service configuration in your default editor, allowing you to make changes, such as modifying the service type to NodePort
``` 
sudo microk8s kubectl edit svc kube-prometheus-stack-prometheus 
``` 
Verify the changes you made to the Prometheus service by listing all services again.
```
sudo microk8s kubectl get svc 
``` 
Check the status of MicroK8s, including enabled addons and running services.
```
sudo microk8s status
``` 
To access the Prometheus dashboard use `Node’s_Public_IP:Nodeport`

 
