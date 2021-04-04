## Run the program

To access Nats inside kubernetes, you need forward ports

```
minikube start
k apply -f nats-depl.yaml
kubectl get pods
k port-forward nats-depl-95f8f556d-2kkk8  4222:4222
```

- first 4222 is port that we access to K8s cluster, second 4222 is NATS server's running port inside the cluster

```
npm run publish
npm run listen
```

## SET UP KUBERNETES

1- install minikube

```
curl -LO https://storage.googleapis.com/minikube/releases/latest/minikube_latest_amd64.deb
sudo dpkg -i minikube_latest_amd64.deb
```

2- start

`minikube start`

gives this error : No possible driver was detected.

3- set the driver

`sudo minikube start --driver=docker`

4- Add your user to the 'docker' group:

`sudo usermod -aG docker $USER && newgrp docker`

6- Install kubectl

```
curl -LO "https://storage.googleapis.com/kubernetes-release/release/$(curl -s https://storage.googleapis.com/kubernetes-release/release/stable.txt)/bin/linux/amd64/kubectl"

```

-Make the kubectl binary executable.

`chmod +x ./kubectl`

- Move the binary in to your PATH.

`sudo mv ./kubectl /usr/local/bin/kubectl`

- check the verison
  `kubectl version`
