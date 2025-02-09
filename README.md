# Test_Fraunhofer
Kubernetes Deployment Projekt

 Übersicht

Dieses Repository enthält die notwendigen Dateien, um eine statische Webanwendung mit Apache in Kubernetes bereitzustellen.Die Anwendung wird mit Docker gebaut und in einem Kubernetes-Cluster mit Minikube oder einem anderen Kubernetes-Cluster deployed.

 Voraussetzungen

Bevor du das Projekt deployst, stelle sicher, dass du folgende Software installiert hast:

Docker (https://www.docker.com/)

Kubernetes & kubectl (https://kubernetes.io/)

Minikube (https://minikube.sigs.k8s.io/docs/)

Prüfe die Installation mit:

docker --version
kubectl version --client
minikube version

 Installation & Deployment

1️- Image bauen und auf Docker Hub hochladen

Falls du das Docker-Image neu bauen und hochladen möchtest:

docker build -t dein-dockerhub-benutzer/imagetest:v1 .
docker push dein-dockerhub-benutzer/imagetest:v1

Falls du das bereits gepushte Image nutzen möchtest, kannst du diesen Schritt überspringen.

2️- Minikube starten

Falls Minikube noch nicht läuft:

minikube start

Überprüfe, ob es läuft:

minikube status

3️- Kubernetes Deployment und Service anwenden

Führe die folgenden Befehle aus, um die Anwendung in Kubernetes bereitzustellen:

kubectl apply -f deployment.yaml
kubectl apply -f service.yaml

Überprüfe, ob die Pods korrekt laufen:

kubectl get pods
kubectl get services

Falls ein Problem auftritt, prüfe die Logs:

kubectl logs -l app=Website

4️- Anwendung testen

Um die Anwendung in einem Browser zu öffnen, nutze:

minikube service my-service --url

Falls du den Port manuell weiterleiten möchtest:

kubectl port-forward service/my-service 30010:80

Dann kannst du im Browser auf http://localhost:30010 zugreifen.
