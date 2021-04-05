# RabbitMQ @ OKE

## Objetivo

O objetivo desse how-to é demonstrar a instalação do RabbitMQ dentro de um cluster kubernetes. Através desse empacotamento é possível deixar em execução o Rabbit dentro de um cluster OKE. 

## Pré-requisito

1. Cluster Kubernetes provisiondo no Oracle Cloud Infrastruture <br>
   https://docs.oracle.com/pt-br/iaas/Content/ContEng/Concepts/contengoverview.htm

1.1 OCI CLI instalado e kubeconfig criado localmente

2. helm instalado localmente


## Etapas

Abra o Terminal e ingresse os seguintes comandos:

```
$ alias k=kubectl
```

```
$ helm init --service-account tiller --history-max 200 --upgrade
```

```
$ helm repo add rabbitmq-oke 'https://raw.githubusercontent.com/fcostabr78/oke_helm_rabbitMQ/master/' 
```

```
$ helm repo update
```

```
$ k create ns rabbitmq
```

```
$ helm install --namespace rabbitmq rabbitmq-oke/oke-helm-rabbitmq --set deployment.user=<senha> --set deployment.password=<senha>
```

Será apresentado o status seguinte com comando acima:



:heartpulse:


