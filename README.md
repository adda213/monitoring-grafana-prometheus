monitoring-grafana-prometheus
 
kubeclt create namespace monitoring

kubectl create namespace icgroup

kubectl apply -f ./lab2/postgres

kubectl apply -f ./lab2/odoo

kubectl apply -f ./lab2/pg_admin
kubectl get pods -n icgroup 
![image](https://github.com/adda213/monitoring-grafana-prometheus/assets/123883398/46658500-c114-482d-a9ee-60398b5f6be3)
curl -fsSL -o get_helm.sh https://raw.githubusercontent.com/helm/helm/main/scripts/get-helm-3
chmod 700 get_helm.sh
./get_helm.sh
helm repo add grafana https://grafana.github.io/helm-charts
helm repo add prometheus-community https://prometheus-community.github.io/helm-charts
helm repo update
helm install grafana grafana/grafana -n monitoring
helm install blackbox prometheus-community/prometheus-blackbox-exporter -n monitoring -f lab-1values-blackbox.yaml
helm install kube-state-metrics prometheus-community/kube-state-metrics -n monitoring
helm install node-exporter prometheus-community/prometheus-node-exporter -n monitoring
helm install postgre-exporter prometheus-community/prometheus-postgres-exporter -f lab-1/values-postgre-exporter.yaml
kubectl get pods -n monitoring
![image](https://github.com/adda213/monitoring-grafana-prometheus/assets/123883398/a3ef27f0-20bb-421e-b5bd-7b1bdbe8c142)
kubectl get pods -n icgroup
![image](https://github.com/adda213/monitoring-grafana-prometheus/assets/123883398/8be6796d-6093-4c5d-a015-fc9996114450)

access to : "localhost:30008" for prometheus
![image](https://github.com/adda213/monitoring-grafana-prometheus/assets/123883398/91f634b9-5a0b-479c-ae27-42b83bc3d080)

![image](https://github.com/adda213/monitoring-grafana-prometheus/assets/123883398/5a105e77-5f69-473c-a323-8d6d4f462ef2)

access to : "localhost:30009" for prometheus
