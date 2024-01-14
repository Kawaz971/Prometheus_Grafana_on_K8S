#1 
 kubectl apply -f https://raw.githubusercontent.com/prometheus-operator/prometheus-operator/main/bundle.yaml --force-conflicts=true --server-side=true

#2
 Créer le fichier : prometheus_rbac.yaml

#3
 kubectl apply -f prometheus_rbac.yaml

#4
 Creer le fichier : prometheus_instance.yaml

#5
 kubectl apply -f prometheus_instance.yaml

#6
 kubectl port-forward svc/prometheus-operated 9090:9090

#7 Configurer Prometheus pour monitorer les services
 Creer le fichier : service_monitor.yaml

#8 
 kubectl apply -f service_monitor.yaml

#9 Déployer Grafana
 kubectl create deployment grafana --image=docker.io/grafana/grafana:latest 

#10 
 kubectl expose deployment grafana --port 3000

#11
 kubectl port-forward svc/grafana 3000:3000

#12
 Creer fichier : expose_prometheus.yaml

#13
kubectl apply -f expose_prometheus.yaml

#14 Expoxition du Prometheus sur le port 30900
 Enter http://<node_ip>:30900
